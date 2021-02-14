---
title: Docker 環境をステージング環境へ（GCP編）
author: KONNO Kiyotaka
type: post
date: 2019-01-20T04:57:47+00:00
archives:
    - 2019
url: /docker-環境をステージング環境へ（gcp編）/
featured_image: /wp-content/uploads/2019/01/スクリーンショット-2019-01-14-19.23.43.jpg
post_views_count:
  - 556
categories:
  - プログラミング
tags:
  - Docker
  - GCP

---
GCP環境にDockerコンテナを作る方法はいくつかあるようです。  
・GCE（Compute Engine）のVMインスタンス作成時に、コンテナ イメージをデプロイ  
・Google Kubernetes Engine（GKE）にクラスタ環境を構築してデプロイ  
・その他色々・・・  
公式ドキュメントはこちら  
_Compute Engine への Docker コンテナのデプロイ_  
<a rel="noreferrer noopener" target="_blank" href="https://cloud.google.com/compute/docs/instance-groups/deploying-docker-containers?hl=ja&authuser=0">https://cloud.google.com/compute/docs/instance-groups/deploying-docker-containers?hl=ja</a>

で、今回はシンプルそうな、VMインスタンス時にデプロイする方法を試します。  
公式ドキュメントはこちら  
_VM およびマネージド インスタンス グループへのコンテナのデプロイ_  
<a rel="noreferrer noopener" target="_blank" href="https://cloud.google.com/compute/docs/containers/deploying-containers?hl=ja&_ga=2.46174759.-1895702560.1541304432&authuser=0">https://cloud.google.com/compute/docs/containers/deploying-containers?hl=ja&_ga=2.46174759.-1895702560.1541304432</a>  
ですが、どうも分かりにくい。いくつか試してくれているサイトがありますが、どうも面倒なようにしか見えない・・・

インスタンス作成時は、Always Freeの条件

<blockquote class="wp-block-quote">
  <p>
    f1-micro インスタンス（1 か月あたり、バージニア州北部 [us-east4] を除く米国リージョンのみ）<br />
  </p>
</blockquote>

を踏まえて。

ただこれ、イメージは一つだけなんですね。後から追加できるかな・・・とりあえず、DBのイメージだけ指定します。

とりあえず、起動はします。  
DBだけだと動いているか分かりませんが、SSHで入って確認してみます。  
入ると

<blockquote class="wp-block-quote">
  <p>
    ########################[ Welcome ]########################<br /> # You have logged in to the guest OS. #<br /> # To access your containers use &#8216;docker attach&#8217; command #<br /> ###########################################################<br />
  </p>
</blockquote>

と表示されています。

<blockquote class="wp-block-quote">
  <p>
    docker images
  </p>
</blockquote>

で目的のイメージが入っていることが確認できます。  
であれば、もう一つのイメージはpullを叩いても良いか。  
で、pullコマンドはContainer Registryの画面で表示させることができるというので、見に行ってみると、<figure class="wp-block-image">

<img src="/uploads/2019/01/スクリーンショット-2019-01-20-12.53.01.jpg?fit=1024%2C363&ssl=1" alt="" class="wp-image-2715" srcset="/uploads/2019/01/スクリーンショット-2019-01-20-12.53.01.jpg?w=1200&ssl=1 1200w, /uploads/2019/01/スクリーンショット-2019-01-20-12.53.01.jpg?resize=300%2C106&ssl=1 300w, /uploads/2019/01/スクリーンショット-2019-01-20-12.53.01.jpg?resize=768%2C272&ssl=1 768w, /uploads/2019/01/スクリーンショット-2019-01-20-12.53.01.jpg?resize=1024%2C363&ssl=1 1024w" sizes="(max-width: 1000px) 100vw, 1000px" /> </figure> 

「pullコマンドを表示」だけでなく「GCEにデプロイ」という魅力的なメニュー。試してみようとしましたが、新しいインスタンスをもう一つ作ることになるようです。  
ということで、pullコマンドをコピーして実行。  
・・・こちらでも認証が必要と言われる、しかも、この環境にはgcloudは入っていない。となる作戦は変わってきます。  
というか、

<blockquote class="wp-block-quote">
  <p>
    各 VM インスタンスにデプロイできるコンテナは 1 つのみです。1 つの VM インスタンスに複数のコンテナをデプロイする必要がある場合は、Kubernetes Engine を検討してください。 複数のコンテナを Compute Engine インスタンスにデプロイする必要がある場合は、チームにお問い合わせください。
  </p>
  
  <p>
  </p>
</blockquote>

です。

## GKE  


一瞬考えましたが、結局インスタンスは複数必要になるのでは。  
ということで、見送り。

## 結論

であれば、結局、普通にGCE（じゃなくてもよいけど）にDocker-composeインストールして、作ったイメージを使えば良いのでは。でも、またプライベートでのイメージを引っ張ってくるところで泣きそうなので、それはもう少しDockerの理解をしてからにすることにして、普通の公開イメージで環境を作って、いじったところを反映する形にしようかなという結論に至りました。  
ダメですね・・・