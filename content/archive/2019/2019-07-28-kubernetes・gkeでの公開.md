---
title: Kubernetes・GKEでの公開
author: KONNO Kiyotaka
type: post
date: 2019-07-28T01:01:12+00:00
url: /kubernetes・gkeでの公開/
featured_image: /wp-content/uploads/2018/11/imac-300x300.jpg
post_views_count:
  - 801
categories:
  - プログラミング
tags:
  - Docker
  - GCP

---
続きます。<figure class="wp-block-embed-wordpress wp-block-embed is-type-wp-embed is-provider-programmers-office">

<div class="wp-block-embed__wrapper">
  <blockquote class="wp-embedded-content" data-secret="J4DAgpeemK">
    <a href="https://www.programmers-office.ml/docker-%e3%82%a4%e3%83%a1%e3%83%bc%e3%82%b7%e3%82%99%e3%82%92-google-container-registry-%e3%81%ab%e7%99%bb%e9%8c%b2/">Docker イメージを Google Container Registry に登録</a>
  </blockquote>
</div></figure> 

## kubectl で設定を行うためのyamlファイル作成

上記でGoogle Container Registryに登録したDockerイメージをGKE（GCP の Kubernetes Engine）で公開します。

今回は、APIだけを公開するということで、API用のファイルだけ作成します。

内容は、基本的には、githubの方を参照しています。

<a rel="noreferrer noopener" aria-label=" (opens in a new tab)" href="https://github.com/pco2699/NullSuck-AI/tree/master/k8s" target="_blank">https://github.com/pco2699/NullSuck-AI/tree/master/k8s</a>

また、イングレス用ファイルは下記のような感じで作りました。  
k8s/api/api-ingress.yml

<pre class="wp-block-code"><code>apiVersion: extensions/v1beta1
kind: Ingress
metadata:
  name: api-ingress
spec:
  rules:
      - http:
        paths:
          - path: /*
            backend:
              serviceName: api-svc
              servicePort: 5432</code></pre>

## GKE周りの設定

これを適用するにあたり、まずは準備ということで、

<pre class="wp-block-code"><code>gcloud container clusters create nullsuck --num-nodes 2
--zone asia-northeast1-a</code></pre>

を実行するとなっていますが、エラー。

<pre class="wp-block-code"><code>ERROR: (gcloud.container.clusters.create) ResponseError: code=403, message=Kubernetes Engine API is not enabled for this project. Please ensure it is enabled in Google Cloud Console and try again: visit https://console.cloud.google.com/apis/api/container.googleapis.com/overview?project=nullsuck-247713 to do so.</code></pre>

先に、Kubernetes Engine APIを有効にしましょう。メッセージに記載されているURLからボタン押すだけです。  
で、続けますが、

<pre class="wp-block-code"><code>gcloud container clusters get-credentials nullsuck</code></pre>

<pre class="wp-block-code"><code>ERROR: (gcloud.container.clusters.get-credentials) One of [--zone, --region] must be supplied: Please specify location.</code></pre>

gcloud config list で現在の状況を確認すると、確かにゾーン・リージョンの設定がないので、  
<a rel="noreferrer noopener" aria-label=" (opens in a new tab)" href="https://cloud.google.com/compute/docs/regions-zones/changing-default-zone-region?hl=ja" target="_blank">https://cloud.google.com/compute/docs/regions-zones/changing-default-zone-region?hl=ja</a>  
デフォルトのゾーンまたはリージョンの変更  
にしたがって設定しましたが、これでは読み込んでくれませんでした。

ですので、コマンドで設定します。

<pre class="wp-block-code"><code>gcloud config set compute/region asia-northeast1
gcloud config set compute/zone asia-northeast1-a</code></pre>

で、本にはありませんが、

<pre class="wp-block-code"><code>gcloud components install kubectl</code></pre>

で、kubectlをインストールして、これも、本のコマンドはyamlファイルの拡張子が違うので要注意ですが、

<pre class="wp-block-code"><code>kubectl apply -f k8s/api/api-deployment.yml
kubectl apply -f k8s/api/api-service.yml
kubectl apply -f k8s/api/api-ingress.yml</code></pre>

ただ、これだと、

<pre class="wp-block-code"><code>error: error validating "k8s/api/api-ingress.yml": error validating data: [ValidationError(Ingress.spec.rules[0].http): unknown field "backend" in io.k8s.api.extensions.v1beta1.HTTPIngressRuleValue, ValidationError(Ingress.spec.rules[0].http): missing required field "paths" in io.k8s.api.extensions.v1beta1.HTTPIngressRuleValue]; if you choose to ignore these errors, turn validation off with --validate=false</code></pre>

と言われてしまったので、

<pre class="wp-block-code"><code>kubectl apply -f k8s/api/api-ingress.yml --validate=false</code></pre>

とすることで、とりあえず一式できました。

ただ、これによりできている、二つのコンテナ api と cloudsql-proxy は、どちらも、ContainerCreating となってしまっています。  
詳細を見ると、secrets &#8220;cloudsql-instance-credentials&#8221; not found　となってしまっているので、それが原因ではないかと思いますが、「GKE の Secret はのちほど設定します」とのことなので、もう少し進めてみます。

## **Cloud SQL** の設定・**Credientials** の設定

SQLサービスは、いきなり

<pre class="wp-block-code"><code>gcloud beta sql instances create nullsuck-db --tier=db-f1-micro --activation-policy=ALWAYS</code></pre>

で、作成を開始してくれますが、しばらくすると、

<pre class="wp-block-code"><code>ERROR: (gcloud.beta.sql.instances.create) Operation https://www.googleapis.com/sql/v1beta4/projects/nullsuck-・・・ is taking longer than expected. You can continue waiting for the operation by running `gcloud beta sql operations wait --project ・・・`</code></pre>

というエラーメッセージが表示されます。しかし、これはエラーというよりは、このコマンドとしてのセッションは切ったというだけなので、メッセージの最後に書いてあるコマンドを叩くと、その後の処理状況も確認できます。  
そして、無事作成されていました。

次にrootへのパスワード設定を行いますが、これは

<pre class="wp-block-code"><code>gcloud sql instances set-root-password nullsuck-db --password = xxx</code></pre>

など、マニュアル見ながらいくつかのオプションの書き方等を試してみましたがダメ。最終的には、

<pre class="wp-block-code"><code>gcloud sql users set-password root --host=% --instance=nullsuck-db --prompt-for-password</code></pre>

で成功しました。

その後のsecretの作成は書いてあるままで進みましたので、これで先ほど問題となっていた、cloudsql-instance-credentials も作成されたと思われます。

この辺、ひたすらコマンドで進められるのは良いですね。