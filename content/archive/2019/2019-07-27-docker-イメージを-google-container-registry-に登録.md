---
title: Docker イメージを Google Container Registry に登録
author: KONNO Kiyotaka
type: post
date: 2019-07-26T22:03:18+00:00
url: /docker-イメージを-google-container-registry-に登録/
featured_image: /wp-content/uploads/2019/07/スクリーンショット-2019-07-27-7.00.22.png
post_views_count:
  - 612
categories:
  - プログラミング
tags:
  - GCP

---
時は遡り、画面が何とか動くようになったので、API連携しようとしたものの、失敗して終了していたこちら。<figure class="wp-block-embed-wordpress wp-block-embed is-type-wp-embed is-provider-programmers-office">

<div class="wp-block-embed__wrapper">
  <blockquote class="wp-embedded-content" data-secret="JK7qpYTtNC">
    <a href="https://www.programmers-office.ml/%e3%81%ac%e3%82%8b%e3%81%95%e3%81%8fapi%e9%80%a3%e6%90%ba%ef%bc%88%e5%a4%b1%e6%95%97%ef%bc%89/">ぬるさくapi連携（失敗）</a>
  </blockquote>
</div></figure> 

画面も、色々試せそうになってきたので、とりあえず、APIを公開しようということで、ぬるさく本の「**6.3 Docker** イメージを **Google Container Registry** に登録してみよう 」を試すことにします。

## GCPプロジェクトの作成

既存のアカウントにプロジェクトを追加します。  
プロジェクト名は真似して「nullsuck」、プロジェクトID「nullsuck-xxxxxx」は自動で振られます。

## **Docker** イメージを **push** 

ここで数日を要した・・・

まず、今回はAPI側を公開することにするので、appとなっている部分は全てapiと読み替えて作業します。  
そこを間違えなければ（一旦間違えましたが・・・）、docker build はおそらく問題なし。docker tag は、結論としてはそこの問題ではなかったのですが、本でも、GCPドキュメントでも、プロジェクトIDを含めるように書かれているのですが、本の記述が「nullsuck」と書かれていて、若干混乱。「nullsuck-xxxxxx」の方を記述するようにしました。

そして、gcloud docker &#8212; push をするのですが、まず、この記述は古いようで、現状では、docker pushでやる形になっています。

が、やってみると、

<pre class="wp-block-code"><code>denied: Token exchange failed for project 'nullsuck-247713'. Caller does not have permission 'storage.buckets.create'. To configure permissions, follow instructions at: https://cloud.google.com/container-registry/docs/access-control</code></pre>

で、権限の問題か、ということで、記載されているドキュメントを見て、バケットを作ってみたりとか、色々試してみていたのですが、最終的な問題点は、現在接続しているプロジェクトが、既存のプロジェクトであり、今回作成したnullsuckプロジェクトではない、ということでした。

<pre class="wp-block-code"><code>gcloud config list</code></pre>

でプロジェクトが確認できます。これはdefault構成だったので、新しい構成を作成。

<pre class="wp-block-code"><code>gcloud config configurations create nullsuck</code></pre>

そして、gcloud initは、対話式で聞いてくれるので、nullsuckプロジェクトを指定することにより、環境が切り替わります。

そこで改めて、docker pushをすると、今度は成功しました。

公開設定が「非公開」になっているのが、本とは異なるので、若干気になる・・・<figure class="wp-block-image">

<img src="https://i0.wp.com/www.programmers-office.ml/wp-content/uploads/2019/07/スクリーンショット-2019-07-27-7.00.22.png?ssl=1" alt="" class="wp-image-3139" srcset="https://i0.wp.com/www.programmers-office.ml/wp-content/uploads/2019/07/スクリーンショット-2019-07-27-7.00.22.png?w=800&ssl=1 800w, https://i0.wp.com/www.programmers-office.ml/wp-content/uploads/2019/07/スクリーンショット-2019-07-27-7.00.22.png?resize=300%2C97&ssl=1 300w, https://i0.wp.com/www.programmers-office.ml/wp-content/uploads/2019/07/スクリーンショット-2019-07-27-7.00.22.png?resize=768%2C248&ssl=1 768w" sizes="(max-width: 800px) 100vw, 800px" data-recalc-dims="1" /> </figure>