---
title: GCE（Google Compute Engine）上のMariaDBに外部から接続
author: KONNO Kiyotaka
type: post
date: 2018-07-06T09:16:43+00:00
archives:
    - 2018
url: /gce（google-compute-engine）上のmariadbに外部から接続/
post_views_count:
  - 1470
categories:
  - プログラミング

---
## GCPのファイアウォール

GCEにインストールしたMariaDBに、その中のWordPressから接続できていますが、ここにプラグイン用のテーブルを追加したり、データをいじったりしたい。

その際に、全てコマンドベースでやるのもつらいし、さらにphpMyAdminをインストールするのもはまりそうな匂いがプンプン。

ということで、ローカルのツールから接続することにします。

まずは、GCPのファイアウォールルール追加です。  
場所は、VPCネットワークの中にあります。  
設定するのは、上りで、tcp:3306を許可します。

しかし、これだけではつながりません。

## リスナー追加

netstat -tlpn  
を叩くと、  
Proto Recv-Q Send-Q Local Address&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Foreign Address&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; State&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; PID/Program name  
tcp&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 0&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 0 127.0.0.1:3306&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 0.0.0.0:*&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; LISTEN&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &#8211;

と表示されます。

これだと、ローカルからしか接続できないわけです。  
これを変更するためには、bind-addressの記述をコメントアウトする、という情報が見つかります。  
問題は、この記述がどこにあるかです。  
結論としては、

/etc/mysql/mariadb.conf.d/50-server.cnf  
にありました。  
これを修正して、sudo /etc/init.d/mysql restart　すると、  
tcp6&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 0&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 0 :::3306&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; :::*&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; LISTEN&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &#8211;  
となってくれました。

しかし、実はこれでもつながりませんでした。

select user, host from mysql.user;すると  
+&#8212;&#8212;&#8212;&#8212;&#8212;+&#8212;&#8212;&#8212;&#8211;+  
| user&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | host&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; |  
+&#8212;&#8212;&#8212;&#8212;&#8212;+&#8212;&#8212;&#8212;&#8211;+  
| hoge&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | localhost |  
| xxxxxxxxxxxxx | localhost |  
| root&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | localhost |  
+&#8212;&#8212;&#8212;&#8212;&#8212;+&#8212;&#8212;&#8212;&#8211;+  
というユーザしかありません。  
で、先に、grant all privileges on \*.\* to konnokiyotaka@&#8217;（接続元）&#8217;;　をしたのですが、これだとユーザが追加されますが、パスワードは指定していない形になっています。  
今回は、この後、SET PASSWORD FOR・・・を行いました。本当は、最初からちゃんとユーザを作ればよいでしょう。

ということで、データメンテもできるようになりました。

## A5:SQL Mk-2

ところで、ローカルのDBメンテツールとして、最強はA5:SQL Mk-2だと思っています。

<a title="https://a5m2.mmatsubara.com/" href="https://a5m2.mmatsubara.com/" target="_blank">https://a5m2.mmatsubara.com/</a>

各種DBへの接続に対応していますし、一番よく使うのは、SQLの整形とか。

英語版も提供されているので、海外にも広まってほしいなと思っています。





<div class="kaerebalink-box" style="text-align: left; overflow: hidden; padding-bottom: 20px; font-size: small; -ms-zoom: 1;">
  <div class="kaerebalink-image" style="margin: 0px 15px 10px 0px; float: left;">
    <a href="https://www.amazon.co.jp/exec/obidos/ASIN/4295000795/jqinglong-22/" target="_blank"><img style="border: currentcolor; border-image: none;" src="https://i2.wp.com/images-fe.ssl-images-amazon.com/images/I/610sYAwscHL._SL160_.jpg?ssl=1" data-recalc-dims="1" /></a>
  </div>
  
  <div class="kaerebalink-info" style="line-height: 120%; overflow: hidden; -ms-zoom: 1;">
    <div class="kaerebalink-name" style="line-height: 120%; margin-bottom: 10px;">
      <a href="https://www.amazon.co.jp/exec/obidos/ASIN/4295000795/jqinglong-22/" target="_blank">いちばんやさしいWordPressの教本第3版 人気講師が教える本格Webサイトの作り方 (「いちばんやさしい教本」)</a></p>
      <div class="kaerebalink-powered-date" style="line-height: 120%; font-family: verdana; font-size: 8pt; margin-top: 5px;">
        posted with <a href="https://kaereba.com" target="_blank" rel="nofollow">カエレバ</a>
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