---
title: DockerでMagento環境を構築する
author: KONNO Kiyotaka
type: post
date: 2019-01-06T09:52:07+00:00
archives:
    - 2019
url: /dockerでmagento環境を構築する/
featured_image: /wp-content/uploads/2019/01/2019-01-06-18.50.10.png
post_views_count:
  - 881
categories:
  - プログラミング
tags:
  - Docker
  - Magento

---
 

Dockerで、ビジュアルに、Magento環境を構築していきたいと思います。

## 参考情報

<a rel="noreferrer noopener" target="_blank" href="https://qiita.com/kzkiq2nd/items/29f69c156f6f6e2fb215">https://qiita.com/kzkiq2nd/items/29f69c156f6f6e2fb215</a>  
を入り口として、  
<a rel="noreferrer noopener" target="_blank" href="https://qiita.com/kzkiq2nd/items/b8162cfc41d13616f861">https://qiita.com/kzkiq2nd/items/b8162cfc41d13616f861</a>  
<a rel="noreferrer noopener" target="_blank" href="https://principle-works.jp/blog/how2runm2ondocker-apache/">https://principle-works.jp/blog/how2runm2ondocker-apache/</a>  
<a rel="noreferrer noopener" target="_blank" href="https://principle-works.jp/blog/how2runm2ondocker-compose/">https://principle-works.jp/blog/how2runm2ondocker-compose/</a>  
も参照。  
しつつ、いかにビジュアルに構築するかを考えます。

## イメージ検索

まずは、Kitematic内で検索してみます。  
最初は、一つしかヒットしなかった気がしたのですが、気のせい？？  
まあまあ、結構な数がヒットします。<figure class="wp-block-image">

<img src="/uploads/2019/01/2019-01-06-8.57.36.png?resize=1024%2C680&#038;ssl=1" alt="" class="wp-image-2585" srcset="/uploads/2019/01/2019-01-06-8.57.36.png?resize=1024%2C680&ssl=1 1024w, /uploads/2019/01/2019-01-06-8.57.36.png?resize=300%2C199&ssl=1 300w, /uploads/2019/01/2019-01-06-8.57.36.png?resize=768%2C510&ssl=1 768w, /uploads/2019/01/2019-01-06-8.57.36.png?resize=480%2C320&ssl=1 480w, /uploads/2019/01/2019-01-06-8.57.36.png?w=1200&ssl=1 1200w" sizes="(max-width: 1000px) 100vw, 1000px" data-recalc-dims="1" /> </figure> 

  
Googleで「magento docker」で検索した場合は、bitnami/magentoが先頭でヒットします。  
さらに、DevBoxなるものもあるといいます。  
どれを使うべきか。

DevBoxが正攻法のようではあります。  
<a rel="noreferrer noopener" target="_blank" href="https://magento.com/blog/technical/set-your-magento-2-development-environment-faster">https://magento.com/blog/technical/set-your-magento-2-development-environment-faster</a>  
が、最初の参考情報によると、ちょっとフルスペックすぎる感じが無きにしも非ず。  
かつ、2.3には未対応っぽい。

次は、Pulls 1M+ となっていて、利用者の多そうなこちら。  
<a rel="noreferrer noopener" target="_blank" href="https://hub.docker.com/r/alexcheng/magento2">https://hub.docker.com/r/alexcheng/magento2</a>  
解説も丁寧にされているのが好印象。2.3.xとも書いてあるので安心。  
こちらにさらに情報あり。  
<a rel="noreferrer noopener" target="_blank" href="https://microbadger.com/images/alexcheng/magento2">https://microbadger.com/images/alexcheng/magento2</a>

bitnami版も確認。  
<a rel="noreferrer noopener" target="_blank" href="https://hub.docker.com/r/bitnami/magento">https://hub.docker.com/r/bitnami/magento</a>  
利点として書かれているのは、最新版追跡の速さですね。  
こちらにも、いくつかのパターンが置かれています。  
<a rel="noreferrer noopener" target="_blank" href="https://bitnami.com/stack/magento/containers">https://bitnami.com/stack/magento/containers</a>

ちょと悩むところではあるのですが、ブランド名を信じて、bitnamiにしてみます。

## bitnami版magento2のインストール

改めて、Kitematicで「bitnami/magento」で検索し、CREATEボタンを押します。  
しばらくダウンロード画面が表示され、追加されたかと思いきや、エラーメッセージ。<figure class="wp-block-image">

<img src="/uploads/2019/01/2019-01-06-14.07.54.png?resize=1024%2C680&#038;ssl=1" alt="" class="wp-image-2586" srcset="/uploads/2019/01/2019-01-06-14.07.54.png?resize=1024%2C680&ssl=1 1024w, /uploads/2019/01/2019-01-06-14.07.54.png?resize=300%2C199&ssl=1 300w, /uploads/2019/01/2019-01-06-14.07.54.png?resize=768%2C510&ssl=1 768w, /uploads/2019/01/2019-01-06-14.07.54.png?resize=480%2C320&ssl=1 480w, /uploads/2019/01/2019-01-06-14.07.54.png?w=1200&ssl=1 1200w" sizes="(max-width: 1000px) 100vw, 1000px" data-recalc-dims="1" /> </figure> <figure class="wp-block-image"><img src="/uploads/2019/01/2019-01-06-14.09.34.png?resize=1024%2C680&#038;ssl=1" alt="" class="wp-image-2587" srcset="/uploads/2019/01/2019-01-06-14.09.34.png?resize=1024%2C680&ssl=1 1024w, /uploads/2019/01/2019-01-06-14.09.34.png?resize=300%2C199&ssl=1 300w, /uploads/2019/01/2019-01-06-14.09.34.png?resize=768%2C510&ssl=1 768w, /uploads/2019/01/2019-01-06-14.09.34.png?resize=480%2C320&ssl=1 480w, /uploads/2019/01/2019-01-06-14.09.34.png?w=1200&ssl=1 1200w" sizes="(max-width: 1000px) 100vw, 1000px" data-recalc-dims="1" /></figure> 

<blockquote class="wp-block-quote">
  <p>
    Welcome to the Bitnami magento container<br />Subscribe to project updates by watching <a rel="noreferrer noopener" target="_blank" href="https://github.com/bitnami/bitnami-docker-magento">https://github.com/bitnami/bitnami-docker-magento</a><br />Submit issues and feature requests at <a rel="noreferrer noopener" target="_blank" href="https://github.com/bitnami/bitnami-docker-magento/issues">https://github.com/bitnami/bitnami-docker-magento/issues</a><br />ERROR ==> The MAGENTO_DATABASE_PASSWORD environment variable is empty or not set. This environment variable is required for Magento to be properly installed.
  </p>
</blockquote>

メッセージに従い、Kitematicの「Settings」タブで、MAGENTO\_DATABASE\_PASSWORDの値を設定し、そのほか、データベース関連の空白になっている欄に入力し、SAVEhttps://github.com/bitnami/bitnami-docker-magento　を見ると、MYSQL\_CLIENT\_・・・の設定は新たなDBを作るための設定のようなので、４項目削除してSAVE。<figure class="wp-block-image">

<img src="/uploads/2019/01/2019-01-06-14.11.35.png?resize=1024%2C680&#038;ssl=1" alt="" class="wp-image-2588" srcset="/uploads/2019/01/2019-01-06-14.11.35.png?resize=1024%2C680&ssl=1 1024w, /uploads/2019/01/2019-01-06-14.11.35.png?resize=300%2C199&ssl=1 300w, /uploads/2019/01/2019-01-06-14.11.35.png?resize=768%2C510&ssl=1 768w, /uploads/2019/01/2019-01-06-14.11.35.png?resize=480%2C320&ssl=1 480w, /uploads/2019/01/2019-01-06-14.11.35.png?w=1200&ssl=1 1200w" sizes="(max-width: 1000px) 100vw, 1000px" data-recalc-dims="1" /> </figure> 

先に進みますが、今度は、mysql-c INFO Trying to connect to MySQL server　で待ち。  
そもそも、どういう仕組みで起動しているのだろう（特にDB）、というのがわからなかったため、いったんコンテナ削除。

## alexcheng/magento2のインストール

こちらを試してみます。  
ダウンロードしてそのまま、この画面。<figure class="wp-block-image">

<img src="/uploads/2019/01/2019-01-06-15.47.14.png?resize=1024%2C550&#038;ssl=1" alt="" class="wp-image-2589" srcset="/uploads/2019/01/2019-01-06-15.47.14.png?resize=1024%2C550&ssl=1 1024w, /uploads/2019/01/2019-01-06-15.47.14.png?resize=300%2C161&ssl=1 300w, /uploads/2019/01/2019-01-06-15.47.14.png?resize=768%2C413&ssl=1 768w, /uploads/2019/01/2019-01-06-15.47.14.png?w=1200&ssl=1 1200w" sizes="(max-width: 1000px) 100vw, 1000px" data-recalc-dims="1" /> </figure> 

すげっ。  
Step 2: Add a Database は、どうするんだっけ、と思いながら、とりあえずは、ドキュメントに記載されているデフォルト情報を設定してみます。  
しかし、「SQLSTATE\[HY000\] \[2002\] No such file or directory」エラー  
Database Server Hostを127.0.0.1にすると「SQLSTATE\[HY000\] \[2002\] Connection refused」になるので、ここの問題っぽい。というか、結局MySQLが動いていないのでは疑惑。  
すなわち、Kitematicは、docker-compose upをしている訳ではないのだろう、ということで、最初はコマンドを叩くことにする。ビジュアルじゃないけど仕方ない。  
こちらも、Kitematicの画面でコンテナ名の右の×印（stop and remove）で削除。しかし、ふとdocker imagesを叩いてみると、どちらも残っている。  
docker ps、docker ps -a では何も出てこないので、docker rmi で削除する。

## bitnami版magento2をcompose

では、改めて、bitnami版でやってみます。  
ユーザホームに作ってしまいます。

<blockquote class="wp-block-quote">
  <p>
    mkdir docker<br />mkdir docker/magento2<br />cd docker/magento2/<br />curl -sSL <a rel="noreferrer noopener" target="_blank" href="https://raw.githubusercontent.com/bitnami/bitnami-docker-magento/master/docker-compose.yml">https://raw.githubusercontent.com/bitnami/bitnami-docker-magento/master/docker-compose.yml</a> > docker-compose.yml<br />
  </p>
</blockquote>

ymlはこのままでも使えそう。

<blockquote class="wp-block-quote">
  <p>
    docker-compose up -d
  </p>
</blockquote>

インストールは無事完了  
いきなり、ここまで来ます。ひえー。<figure class="wp-block-image">

<img src="/uploads/2019/01/2019-01-06-17.29.15.png?resize=1024%2C717&#038;ssl=1" alt="" class="wp-image-2591" srcset="/uploads/2019/01/2019-01-06-17.29.15.png?resize=1024%2C717&ssl=1 1024w, /uploads/2019/01/2019-01-06-17.29.15.png?resize=300%2C210&ssl=1 300w, /uploads/2019/01/2019-01-06-17.29.15.png?resize=768%2C538&ssl=1 768w, /uploads/2019/01/2019-01-06-17.29.15.png?w=1200&ssl=1 1200w" sizes="(max-width: 1000px) 100vw, 1000px" data-recalc-dims="1" /> </figure> <figure class="wp-block-image"><img src="/uploads/2019/01/2019-01-06-17.34.55.png?resize=1024%2C908&#038;ssl=1" alt="" class="wp-image-2594" srcset="/uploads/2019/01/2019-01-06-17.34.55.png?resize=1024%2C908&ssl=1 1024w, /uploads/2019/01/2019-01-06-17.34.55.png?resize=300%2C266&ssl=1 300w, /uploads/2019/01/2019-01-06-17.34.55.png?resize=768%2C681&ssl=1 768w, /uploads/2019/01/2019-01-06-17.34.55.png?w=1200&ssl=1 1200w" sizes="(max-width: 1000px) 100vw, 1000px" data-recalc-dims="1" /></figure> 

ただ、ymlはこれではダメです。DB永続化のためにdata volumesにホスト側のディレクトリを指定する必要があります（下に書くなら最初から書いてくれー）。  
mkdir mariadb-persistence  
mkdir magento-persistence  
ここへのパスに書き換え、最後のvolumes指定を削除して、実行。  
こんな感じでファイルが作成されます。<figure class="wp-block-image">

<img src="/uploads/2019/01/2019-01-06-17.50.08.png?ssl=1" alt="" class="wp-image-2595" srcset="/uploads/2019/01/2019-01-06-17.50.08.png?w=300&ssl=1 300w, /uploads/2019/01/2019-01-06-17.50.08.png?resize=227%2C300&ssl=1 227w" sizes="(max-width: 300px) 100vw, 300px" data-recalc-dims="1" /> </figure> 

無事画面も表示されます。管理画面はuserでログインします。パスワードを確認するために、Kitematicを起動し、magento側（非mariadb側）のSettingsで確認します。

と言う感じで、無事開発環境構築ができました。  
長かった！