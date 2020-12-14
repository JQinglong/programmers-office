---
title: GCE（Google Compute Engine）へのWordPressインストール（2）
author: KONNO Kiyotaka
type: post
date: 2018-07-03T20:50:34+00:00
archives:
    - 2018
url: /gce（google-compute-engine）へのwordpressインストール（2）/
post_views_count:
  - 1446
categories:
  - プログラミング

---
今回でWordPressインストールまでたどり着こう。  
参考は、こちら。  
<a title="https://qiita.com/yuichiyuichi447/items/4bb3b9dbb69ee5a693cf" href="https://qiita.com/yuichiyuichi447/items/4bb3b9dbb69ee5a693cf" target="_blank" rel="noopener">https://qiita.com/yuichiyuichi447/items/4bb3b9dbb69ee5a693cf</a>

## GCEへのApacheインストール

これは  
sudo apt install apache2  
だけ。  
ただ、この時点でちゃんと動作を確認すべき・・・

## GCEへのPHP7インストール

sudo apt install -y php php-mysql libapache2-mod-php

ここでも、動作確認すべき。

## GCEへのWordpressインストール

さらに、こちらを参考。  
<a title="https://qiita.com/seijikohara/items/f34753b2a783e03d7db4" href="https://qiita.com/seijikohara/items/f34753b2a783e03d7db4" target="_blank" rel="noopener">https://qiita.com/seijikohara/items/f34753b2a783e03d7db4</a>

/etc/apache2/apache2.conf  
へのWPインストール先追記は、あえて自分のHOME配下に変更。

そして、そのディレクトリを作成しておく。

curl -O https://raw.githubusercontent.com/wp-cli/builds/gh-pages/phar/wp-cli.phar  
こちらでは、curlを使用。wgetとはあまり差はないのですかね。趣味の範囲？

wp core download &#8211;locale=ja &#8211;path=/var/www/html/wordpress &#8211;allow-root  
を叩くときに、apache2.confで指定したパスに変更。  
また、wp-config.phpの修正で、AUTH_KEY等はコピペが必要です。  
この際、AWS Cloud9でviに張り付ける場合は、右クリックコピーではダメで、必ずCtrl-C Ctrl-Vです。

また、いつも忘れますが、viで複数行削除は、

  1. 削除範囲の開始行で「ms」
  2. 削除範囲の終了行で「me」
  3. 「:&#8217;s,&#8217;ed」と入力し、Enter

です。

さて、これで動くと思いきや、そうは問屋が卸さないのがいつものこと。

まず、手順を二つ参照したために、そもそもWP用のDBを作る作業が抜けていました。  
これは  
CREATE DATABASE xxx DEFAULT CHARACTER SET utf8 COLLATE utf8\_unicode\_ci;  
GRANT ALL ON xxx.* TO &#8216;xxx&#8217;@&#8217;localhost&#8217;;  
だけしておけばOK。

しかし、wp option get homeを叩くと  
Error: The site you have requested is not installed.  
Run \`wp core install\` to create database tables.  
という状況。  
ちょっと混乱しますが、今回はwp core installを叩くのではなく（ここがちょっと他のページも含めて分かりにくい）、Web画面のインストーラを実行する想定と思われる。  
しかし、Web画面を開こうとすると、403エラー。

ここでかなり苦戦しました。だから、Apache、PHPそれぞれインストールしたら一つずつ動作確認はしておいて、問題の切り分けをしやすくしておくべき。

結論としては、/etc/apache2/apache2.confに  
<Directory /xxx/xxx/xxx>  
AllowOverride All  
</Directory>  
という記載を行うのですが、AllowOverride Allの下に、Require all grantedも必要でした。  
全く違うディレクトリを指定したためですね。

と色々大変でしたが、Webのインストーラが動き、WordPressもインストール完了です。

<div class="kaerebalink-box" style="text-align: left; overflow: hidden; padding-bottom: 20px; font-size: small; -ms-zoom: 1;">
  <div class="kaerebalink-image" style="margin: 0px 15px 10px 0px; float: left;">
    <a href="https://www.amazon.co.jp/exec/obidos/ASIN/4295000795/jqinglong-22/" target="_blank" rel="noopener"><img style="border: currentcolor;" src="https://i2.wp.com/images-fe.ssl-images-amazon.com/images/I/610sYAwscHL._SL160_.jpg?ssl=1" data-recalc-dims="1" /></a>
  </div>
  
  <div class="kaerebalink-info" style="line-height: 120%; overflow: hidden; -ms-zoom: 1;">
    <div class="kaerebalink-name" style="line-height: 120%; margin-bottom: 10px;">
      <a href="https://www.amazon.co.jp/exec/obidos/ASIN/4295000795/jqinglong-22/" target="_blank" rel="noopener">いちばんやさしいWordPressの教本第3版 人気講師が教える本格Webサイトの作り方 (「いちばんやさしい教本」)</a></p>
      <div class="kaerebalink-powered-date" style="line-height: 120%; font-family: verdana; font-size: 8pt; margin-top: 5px;">
        posted with <a href="https://kaereba.com" target="_blank" rel="nofollow noopener">カエレバ</a>
      </div>
    </div>
    <div class="kaerebalink-detail" style="margin-bottom: 5px;">
      石川栄和,大串 肇,星野邦敏 インプレス 2017-02-24
    </div>
    <div class="kaerebalink-link1" style="margin-top: 10px;">
    </div>
  </div>
  
  <div class="booklink-footer" style="clear: left;">
  </div>
</div>