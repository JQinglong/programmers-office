---
title: Docker 環境をステージング環境へ（Docker pull編）part1
author: KONNO Kiyotaka
type: post
date: 2019-01-14T14:36:14+00:00
archives:
    - 2019
url: /docker-環境をステージング環境へ（docker-pull編）part1/
featured_image: /wp-content/uploads/2019/01/スクリーンショット-2019-01-14-19.23.43.jpg
post_views_count:
  - 632
categories:
  - プログラミング
tags:
  - Docker

---
docker pushができたので、今度は、サーバ側からpullします。  
サーバは、GCPのつもりでしたが、Mgentoの検証を行っていたAWSを使うか、と考え、それならば、Elastic Container Serviceを使ってみることにします。

## Elastic Container Service（ECS）

まず、ECSには二つの起動モデルがあります。  
・Fargate 起動タイプモデル  
・EC2 起動タイプモデル  
Fargateはコンテナ用のリソースで、EC2とは切り離されており、それ用の料金が発生します。逆に言えば、コンテナを使うためにEC2を増強するための料金は不要ということです。これに対して、EC2起動モデルの場合は、ECSの料金は不要です。  
今回は、EC2の１年間無料枠を利用して、EC2起動タイプで行ってみます。  
（AWSもDockerも初心者なのに大丈夫かどうかは不明です）

ECSの手順については、こちらを参照させていただきました。  
<a rel="noreferrer noopener" target="_blank" href="https://dev.classmethod.jp/cloud/aws/amazon-ecs-entrance-1/">https://dev.classmethod.jp/cloud/aws/amazon-ecs-entrance-1/</a>  
最初の、タスク定義を作成するところで、FARGATEかEC2かを選択するボタンがあるので、EC2を選択します。  
タスク定義名は、タスク定義で指定する内容が、使用するDockerイメージだったり、ということなので、WooCommerceとしておきます。  
他は初期値のままで「コンテナの追加」をします。  
今回は、woocommerce\_mariadb\_1、woocommerce\_wordpress\_1として、二つ分追加します。  
ポートマッピングは悩みますが、mariadb側はなし、wordpress側は80:80と、443:443を追加しておきます。  
タスク定義が正常に作成されました、とのことです。<figure class="wp-block-image">

<img src="/uploads/2019/01/スクリーンショット-2019-01-14-22.27.42.jpg?ssl=1" alt="" class="wp-image-2696" srcset="/uploads/2019/01/スクリーンショット-2019-01-14-22.27.42.jpg?w=800&ssl=1 800w, /uploads/2019/01/スクリーンショット-2019-01-14-22.27.42.jpg?resize=300%2C182&ssl=1 300w, /uploads/2019/01/スクリーンショット-2019-01-14-22.27.42.jpg?resize=768%2C465&ssl=1 768w" sizes="(max-width: 800px) 100vw, 800px" data-recalc-dims="1" /> </figure> 

続いて、クラスターを作成します。  
クラスターテンプレートは、Fargateではないので、「EC2 Linux + ネットワーキング」を指定します。  
インスタンスタイプは無料枠なので、t2.micro、キーペアは作成済みのものを選択します。  
「コンテナインスタンスの IAM ロール」はさらに不明なので、「新しいロールの作成」のまま進めます。  
分からないながら進めていき、起動します。  
「サービスの検出の統合の有効化」はさらに不明のため、チェックを外しておきます。（上記サイトの絵にはありませんので、貼っておきます）<figure class="wp-block-image">

<img src="/uploads/2019/01/スクリーンショット-2019-01-14-22.46.38.jpg?ssl=1" alt="" class="wp-image-2698" srcset="/uploads/2019/01/スクリーンショット-2019-01-14-22.46.38.jpg?w=800&ssl=1 800w, /uploads/2019/01/スクリーンショット-2019-01-14-22.46.38.jpg?resize=300%2C268&ssl=1 300w, /uploads/2019/01/スクリーンショット-2019-01-14-22.46.38.jpg?resize=768%2C686&ssl=1 768w" sizes="(max-width: 800px) 100vw, 800px" data-recalc-dims="1" /> </figure> 

以上で立ち上がったはずですが、サービス画面に行ってみると、起動失敗。  
理由は、  
https://registry.gitlab.com/v2/aaa/bbb/woocommerce\_wordpress\_1/manifests/latest: denied: access forbidden  
まあ、そうですよね・・・<figure class="wp-block-image">

<img src="/uploads/2019/01/スクリーンショット-2019-01-14-22.48.31.jpg?ssl=1" alt="" class="wp-image-2699" srcset="/uploads/2019/01/スクリーンショット-2019-01-14-22.48.31.jpg?w=800&ssl=1 800w, /uploads/2019/01/スクリーンショット-2019-01-14-22.48.31.jpg?resize=300%2C146&ssl=1 300w, /uploads/2019/01/スクリーンショット-2019-01-14-22.48.31.jpg?resize=768%2C374&ssl=1 768w" sizes="(max-width: 800px) 100vw, 800px" data-recalc-dims="1" /> </figure> 

コンテナの設定の、「プライベートレジストリの認証」「認証情報パラメータ」辺りだと思いますが、今日は時間切れです。