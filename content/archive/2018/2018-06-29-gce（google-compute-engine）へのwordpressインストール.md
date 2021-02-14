---
title: GCE（Google Compute Engine）へのWordPressインストール（1）
author: KONNO Kiyotaka
type: post
date: 2018-06-29T09:15:47+00:00
archives:
    - 2018
url: /gce（google-compute-engine）へのwordpressインストール/
post_views_count:
  - 1360
categories:
  - プログラミング

---
さて、環境を定めたら、WordPressをインストールします。

## Cloud Launcherではない

GCP・WordPressで検索すると、コンソールのCloud Launcherからインストールする方法が多数ヒットすると思います。  
確かに、メニューから選択して簡単にインストールできそうです。  
[<img style="display: inline; background-image: none;" title="gcp3" src="/uploads/2018/06/gcp3_thumb.png?resize=244%2C198&#038;ssl=1" alt="gcp3" width="244" height="198" border="0" data-recalc-dims="1" />][1]

[<img style="display: inline; background-image: none;" title="gcp1" src="/uploads/2018/06/gcp1_thumb.png?resize=244%2C130&#038;ssl=1" alt="gcp1" width="244" height="130" border="0" data-recalc-dims="1" />][2]  
この流れは魅力的。

しかし、これは、WordPress用にインスタンスを立ち上げるサービスになります。  
そうすると、結局二つ目のインスタンスになってしまい、<a href="https://cloud.google.com/free/docs/always-free-usage-limits#compute_name" target="_blank" rel="noopener">Always Free</a>から外れてしまいます。

今回やりたいのは、既存のGCEインスタンスにWPをインストールするということです。

（完全に言葉が間違っていたので追記）  
GCP（Google Cloud Platform）はGoogleのクラウドの状のサービス諸々ですね。  
ですから、GCP・WordPressで検索すれば当然GCP上にWordPressのサービスを立ち上げる方法がヒットするでしょう。  
GCE（Google Compute Engine）は、GCPのサービスの中の一つで、IaaS環境を提供してくれているというものです。今やろうとしているのは、そのGCE環境の中にWordPressをインストールする、ということなので、GCE・WordPressで検索すべきです。そうすると、もう少し違う情報も出てきます。

## GCEへのMySQLインストール

さて、WordPressをインストールするとなると、必要なのがMySQLです。  
方法としては、外部に接続する方法も「あり」かとは思います。  
元々さくらレンタルサーバに環境作ろうとしたくらいですので、さくらのDBに繋ぎに行ってもよいわけです。  
しかし、ここは、怖いもの見たさで、GCE内にMySQLもインストールします。

そして、ここでも、GCPコンソールから「SQL」という魅力的なアイコンが見えます。  
これをクリックすると、簡単にMySQLがインストールできそうです。

[<img style="display: inline; background-image: none;" title="gcp2" src="/uploads/2018/06/gcp2_thumb.png?resize=244%2C144&#038;ssl=1" alt="gcp2" width="244" height="144" border="0" data-recalc-dims="1" />][3]

しかし、これも、データベース用のインスタンス立ち上げサービスです。  
あくまでも、既存のインスタンス内にインストールしたいので、これは使用しません。

## MariaDB

そこで、一番参考になりそうなのがこちら。  
<a title="https://qiita.com/mekabuko/items/d0ef4492f60e40f84f84" href="https://qiita.com/mekabuko/items/d0ef4492f60e40f84f84" target="_blank" rel="noopener">https://qiita.com/mekabuko/items/d0ef4492f60e40f84f84</a>

そして、MariaDBという名前が気になりつつ、MySQL入っていないかなと思って、mysqlを叩いてみました。

$ mysql  
The program &#8216;mysql&#8217; can be found in the following packages:  
* mysql-client-core-5.7  
* mariadb-client-core-10.0  
Ask your administrator to install one of them

出た、mariadb。MariaDBって何？

基本情報はググれば分かるとして、最近は利用が伸びていて、PL/SQLに対応し始めた、というのが趣深いですね。

ということで、Mariaをインストールすることにします。

上記では、yumでインストールしていますが、こちらの環境はUbuntuなので、sudo apt-get install mariadb-server。

インストール成功しましたが、こちらと同じ状態になっています。  
<a title="https://jyn.jp/ubuntu-16-04-mariadb-password-bug/" href="https://jyn.jp/ubuntu-16-04-mariadb-password-bug/" target="_blank" rel="noopener">https://jyn.jp/ubuntu-16-04-mariadb-password-bug/</a>  
書いていただいている対応により、接続できるようになりました。

&nbsp;

いったん休憩にします。

<div class="kaerebalink-box" style="text-align: left; overflow: hidden; padding-bottom: 20px; font-size: small; -ms-zoom: 1;">
  <div class="kaerebalink-image" style="margin: 0px 15px 10px 0px; float: left;">
    <a href="https://www.amazon.co.jp/exec/obidos/ASIN/4839962340/jqinglong-22/" target="_blank" rel="noopener"><img style="border: currentcolor;" src="https://i0.wp.com/images-fe.ssl-images-amazon.com/images/I/511q0UtqM5L._SL160_.jpg?ssl=1" data-recalc-dims="1" /></a>
  </div>
  
  <div class="kaerebalink-info" style="line-height: 120%; overflow: hidden; -ms-zoom: 1;">
    <div class="kaerebalink-name" style="line-height: 120%; margin-bottom: 10px;">
      <p>
        <a href="https://www.amazon.co.jp/exec/obidos/ASIN/4839962340/jqinglong-22/" target="_blank" rel="noopener">PHP7＋MariaDB／MySQLマスターブック</a>
      </p>
      <div class="kaerebalink-powered-date" style="line-height: 120%; font-family: verdana; font-size: 8pt; margin-top: 5px;">
        posted with <a href="https://kaereba.com" target="_blank" rel="nofollow noopener">カエレバ</a>
      </div>
    </div>
    <div class="kaerebalink-detail" style="margin-bottom: 5px;">
      永田 順伸 マイナビ出版 2018-01-30
    </div>
    <div class="kaerebalink-link1" style="margin-top: 10px;">
    </div>
  </div>
  
  <div class="booklink-footer" style="clear: left;">
  </div>
</div>

 [1]: /uploads/2018/06/gcp3.png?ssl=1
 [2]: /uploads/2018/06/gcp1.png?ssl=1
 [3]: /uploads/2018/06/gcp2.png?ssl=1