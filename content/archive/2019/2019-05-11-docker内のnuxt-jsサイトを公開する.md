---
title: Docker内のNuxt.jsサイトを公開する
author: KONNO Kiyotaka
type: post
date: 2019-05-10T20:49:51+00:00
archives:
    - 2019
url: /docker内のnuxt-jsサイトを公開する/
featured_image: /wp-content/uploads/2019/05/NuxtTypeScriptStarter.png
post_views_count:
  - 710
categories:
  - プログラミング
tags:
  - Docker
  - GCP
  - Nuxt.js

---
Docker内に構築したNuxt.jsのサイトを公開する、条件として、公開サイトもDockerで構築し、かつ、ソースはボリューム機能でDocker外と共有とする。無料で。  
なかなかハードルが高かったですが、できました！

## Docker環境をどこに公開するか

無料公開と考えた場合に、1年の期間制限のAWSは対象から外します。そして、本サイト自体がGCEで立っているので、一旦それも除外。そこで検討したのが、Azureです。

### Azure App Service

Azureでは、素のApp Serviceは無料プランがあります。

App Service の価格  
<a rel="noreferrer noopener" aria-label=" (opens in a new tab)" href="https://azure.microsoft.com/ja-jp/pricing/details/app-service/windows/" target="_blank">https://azure.microsoft.com/ja-jp/pricing/details/app-service/windows/</a>

この素のサービスはPaaSなので、Dockerをインストールして環境構築するということはできません。これと連携してコンテナを読み込む、<a rel="noreferrer noopener" aria-label=" (opens in a new tab)" href="https://docs.microsoft.com/ja-jp/azure/app-service/containers/app-service-linux-intro" target="_blank">Web App for Containers</a>というサービスがありますが、これは無料プランでは利用できません。さらに、通常であれば利用を検討すべきContainer InstancesとかAKS（Azure Kubernetes Service）というものもありますが、これらも有料プランのみです。

色々苦労した挙句、無料でDockerコンテナを立ち上げるのは無理ということで、あきらめました。

### Heroku

Herokuでもコンテナを読み込んでリリースする機能が提供されています。  
<a href="https://devcenter.heroku.com/articles/container-registry-and-runtime" target="_blank" rel="noreferrer noopener" aria-label=" (opens in a new tab)">https://devcenter.heroku.com/articles/container-registry-and-runtime</a>

これは無料で使えるプランもあるのですが、Volumeはサポートされていません。

なぜVolumeを使いたいかというと、ローカルの開発環境もDockerで構築したい、それと同一の環境をリリース環境に持っていきたい、ただ開発ツールはクライアントに持つことになるのでソースはローカルに持ちたい、そのソースをコミットすることでリリース環境にも反映したい、という理由です。  
そういう意味で、最近話題の、VSCodeのRemote Development機能  
<a rel="noreferrer noopener" aria-label=" (opens in a new tab)" href="https://crieit.net/posts/VSCode-Remote-Development" target="_blank">https://crieit.net/posts/VSCode-Remote-Development</a>  
開発ツールをローカルに持ちつつソースはローカルに持つ必要がないという意味ですごいと思うのですが、複数人開発と考えた時にはどうなんだろうとも思ったりします。

### さくらArukas

<a rel="noreferrer noopener" aria-label=" (opens in a new tab)" href="https://arukas.io/" target="_blank">https://arukas.io/</a>

今回試しませんでしたが、これもHerokuと同様、Volumeはサポートされません。ただ、無料プランが提供されているのは発見でした。

### GCE（Google Compute Engine）

結局VMをそのまま使わせてもらえる環境でなければ今回の条件には合わない、と理解し、そうなると使えるのはGCEしかないのでは、という結論になりました。すでにDocker立てているわけですが、そこはDocker。複数立てることもできるわけです。ということで、もう一つDocker環境を立てることにしました。

## 公開用Docker構築

前回<figure class="wp-block-embed-wordpress wp-block-embed is-type-wp-embed is-provider-programmers-office">

<div class="wp-block-embed__wrapper">
  <blockquote class="wp-embedded-content" data-secret="WI4oM0yuin">
    <a href="https://www.programmers-office.ml/%e3%82%bf%e3%82%a4%e3%82%bf%e3%83%8b%e3%83%83%e3%82%af%e3%82%a2%e3%83%97%e3%83%aa%e3%82%92%e4%bd%9c%e3%82%8d%e3%81%86%ef%bc%88nuxt-js-%e9%96%8b%e7%99%ba%e7%92%b0%e5%a2%83%e3%81%ae%e5%9f%ba%e6%9c%ac/">タイタニックアプリを作ろう（Nuxt.js 開発環境の基本）</a>
  </blockquote>
</div></figure> 

ここではなるべくシンプルなDockerファイルを目指して設定をしましたが、これはDockerをUpした後にサービスを起動しなければならないということです。  
そうではなく、Upと共にNuxtサービスも立ち上げるということで試行錯誤しました。

まず、最初はDocker Build、あるいはUpでのエラー。  
ERROR: Service &#8216;app&#8217; failed to build: containerd-shim not installed on system

DokerファイルをいじるとBuildだけはできたりして、大いに悩みましたが、最終的には、VMリスタートで解消。時間を返せ・・・  
再起動したらしたで、既存のDocker＝本サイトが立ち上がらないという問題発生！原因は、先にApaheが起動していてポート80を取られていたため。サービスを落として再度実行により問題解消。かなりの時間を費やして、やっと本題。

最終的には下記のサイトを大いに参考にさせていただきました。

dockerでnuxt.jsの環境を作ってみる  
<a rel="noreferrer noopener" aria-label=" (opens in a new tab)" href="https://qiita.com/reflet/items/e7c33f84ab43ab237ee4" target="_blank">https://qiita.com/reflet/items/e7c33f84ab43ab237ee4</a>

Dockerfile

<pre class="wp-block-code"><code>FROM node:12.1.0-alpine
WORKDIR /app
RUN npm install --global @vue/cli @vue/cli-init
WORKDIR /app/titanic-client
RUN yarn install
ENV HOST 0.0.0.0
EXPOSE 3000
CMD ["yarn", "run", "dev"]</code></pre>

docker-compose.yml

<pre class="wp-block-code"><code>version: '3'
services:
  app:
    build: ./client
    volumes:
      - ./client:/app
    ports:
      - "3000:3000"
    tty: true</code></pre>

ポイントとしては、

  * vue/cli だけでなく、vue/cli-initもインストールしておくことが必要
  * yarn installはpackage.jsonが存在するディレクトリで実行する必要があり、nuxtアプリを下位階層に作る場合（vue initでアプリ名を指定する場合：今回はtitanic-client）はディレクトリ切り替えのために、WORKDIRを指定する。
  * CMD [&#8220;yarn&#8221;, &#8220;run&#8221;, &#8220;dev&#8221;]によりDocker起動時にNuxtアプリも起動する

という感じでしょうか。終わってしまえば結構シンプルにできることがわかりますが、ここまで来るのは大変でした。

これで立ち上がれば、GCEの公開アドレスのポート3000で、例の変な画面が見えるようになります。