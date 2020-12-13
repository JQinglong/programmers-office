---
title: Docker 環境をステージング環境へ（Docker push編）
author: KONNO Kiyotaka
type: post
date: 2019-01-14T10:25:10+00:00
url: /docker-環境をステージング環境へ（docker-push編）/
featured_image: /wp-content/uploads/2019/01/スクリーンショット-2019-01-14-19.23.43.jpg
post_views_count:
  - 585
categories:
  - プログラミング
tags:
  - Docker

---
まだ、全然途中ですが、いったんベンダー機能とショップ画面が見えるようになったところで、これを別サーバ（ステージング環境のつもり）に持っていきたいと思います。  
Docker力強化の目的もあります。

## Docker イメージのレジストリサービス

ローカル開発環境のDockerイメージを別サーバに持っていくために、まずは、Dockerイメージを共有することが必要と考えます。すると、レジストリサービスが必要ということが分かります。  
そしてレジストリサービスを調べてみると、ありがたいサービスが提供されていることが分かります。  
・Docker Hub  
・Amazon Elastic Container Registry (ECR)  
・Google Container Registry  
・Azure Container Registry  
・GitLab Container Registry  
などなど。

構築先がGCPなのと、このサービスもAlways Free対象なので、Googleも有力な候補ではありますが、ソースをGit管理するなら、同じ管理にするのが合理的なのではということと、GitはGitLab派の私としては、GitLab Container Registryを使ってみることとします。

## GitLab Container Registryへのpush

流れとしては、まずcommitして、イメージ作成。  
これは、こちらを参照  
<a rel="noreferrer noopener" target="_blank" href="https://www.memotansu.jp/docker/626/">https://www.memotansu.jp/docker/626/</a>

commitなの、buildなの、というのはよく分かっていませんが、とりあえず、これで行ってみます。

<blockquote class="wp-block-quote">
  <p>
    docker login registry.gitlab.com<br />
  </p>
</blockquote>

ログインはできます。  
しかし、pushは、3つあるイメージのうちの2つをpushしたいわけで、その仕組みがいまいち分かりません。  
gitlabのページに記載を参考に、最後に「:タグ名」を付けてみても、  
「An image does not exist locally with the tag」  
となります。  
この辺りを参考に、タグ付けします。  
<a rel="noreferrer noopener" target="_blank" href="http://docs.docker.jp/linux/step_six.html">http://docs.docker.jp/linux/step_six.html</a>  
<a rel="noreferrer noopener" target="_blank" href="https://docs.docker.com/engine/reference/commandline/tag/">https://docs.docker.com/engine/reference/commandline/tag/</a>  
そうすると、

<blockquote class="wp-block-quote">
  <p>
    registry.gitlab.com/aaa/bbb/woocommerce_mariadb_1 v1.1 a4e11e5e5b41 3 hours ago 262MB<br />registry.gitlab.com/aaa/bbb/woocommerce_wordpress_1 v1.1 eba2457b8e6a 4 hours ago 438MB
  </p>
</blockquote>

というようなイメージが出来上がります。  
ちょっと分かりづらく苦労しましたが、この状態で、

<blockquote class="wp-block-quote">
  <p>
    docker push registry.gitlab.com/aaa/bbb/woocommerce_mariadb_1:v1.1<br />docker push registry.gitlab.com/aaa/bbb/woocommerce_wordpress_1:v1.1
  </p>
</blockquote>

というようなコマンドを実行します。  


gitlab.comのRegistryリンクからみてみると、こんな表示が二つされるようになりました。<figure class="wp-block-image">

<img src="https://i2.wp.com/www.programmers-office.ml/wp-content/uploads/2019/01/スクリーンショット-2019-01-14-19.09.40.png?fit=1024%2C133&ssl=1" alt="" class="wp-image-2691" srcset="https://i2.wp.com/www.programmers-office.ml/wp-content/uploads/2019/01/スクリーンショット-2019-01-14-19.09.40.png?w=1700&ssl=1 1700w, https://i2.wp.com/www.programmers-office.ml/wp-content/uploads/2019/01/スクリーンショット-2019-01-14-19.09.40.png?resize=300%2C39&ssl=1 300w, https://i2.wp.com/www.programmers-office.ml/wp-content/uploads/2019/01/スクリーンショット-2019-01-14-19.09.40.png?resize=768%2C99&ssl=1 768w, https://i2.wp.com/www.programmers-office.ml/wp-content/uploads/2019/01/スクリーンショット-2019-01-14-19.09.40.png?resize=1024%2C133&ssl=1 1024w" sizes="(max-width: 1000px) 100vw, 1000px" /> </figure> 

ちょっと苦労したので、いったんここまで。