---
title: Monaca Onsen UI V2 Vueで外部JSON取得
author: KONNO Kiyotaka
type: post
date: 2018-07-12T09:11:26+00:00
url: /monaca-onsen-ui-v2-vueで外部json取得/
post_views_count:
  - 1100
categories:
  - プログラミング

---
フロント側画面デザイン作成  
↓  
サーバ側WordPress構築  
↓  
ということで、再度フロント側に戻り、WordPressのデータを参照します。

いやー、あきらめそうになりましたが、かろうじて持ちこたえました。

## $http.getの使用

サンプルを探し始めてすぐに見つかったのが、こちら。  
<a href="https://ja.stackoverflow.com/questions/36496/monaca-onsen-ui-v2-vue-navigation-%e4%b8%8a%e3%81%a7%e3%82%b5%e3%83%bc%e3%83%90%e3%82%b5%e3%82%a4%e3%83%89%e3%81%8b%e3%82%89%e5%8f%96%e5%be%97%e3%81%97%e3%81%9fjson%e3%81%8c%e7%94%bb%e9%9d%a2%e3%81%ab%e5%8f%8d%e6%98%a0%e3%81%95%e3%82%8c%e3%81%aa%e3%81%84" target="_blank" rel="noopener">Monaca Onsen UI V2 Vue Navigation 上でサーバサイドから取得したjsonが画面に反映されない</a>  
この中で使用されているthis.$http.getを使用したいのですが、そのままこの記述を使わせていただくと、  
Cannot read property &#8216;get&#8217; of undefined  
となります。このエラーメッセージも分かりにくいですが、ただ、比較的すぐに、this.$httpが参照できていないということが分かります。

では$httpは何なのかというと、これもvue-resoureぽいな、ということが分かり、Axiosにとって代わられそうだということも分かります。

が、これらをどう参照したらよいのかが分からず、苦労しました。

先に結論を書くと、monacaのターミナルで、npm install axiosを叩きます。

## Vue.js 単一ファイルコンポーネント

結論にたどり着くまでに時間がかかった一つの理由が、多くのサンプルが、単一ファイルコンポーネントの構成を前提にしていないことです。

未だに理解しきっていませんが、単一ファイルコンポーネントの場合は、srcの中で.vueファイルに記述をしていき、Monacaの場合は、保存すると、Webpackが動いてwwwにファイルが作成される、ということのようです。  
ですから、src側に外部ライブラリをセットしなければいけないのでは、と考え、しかし、Monacaで用意されている「JS/CSS コンポーネントの追加と削除」では反映されているように見えないし、と悩みました。

CDNで参照したらどうだろう、なども試しましたがダメでした。  
（逆に、CDNで参照する方法は取れないの？という疑問は残ります・・・）

また、Monacaのターミナル機能は最近の追加機能だと思いますが、それまではどうしていたの？？という疑問も・・・

とりあえずは先に進めるようにはなりましたが、axoss.getでの参照はSSLでの接続が要求されているので、それをどうするか（接続先のWordPressはGCE上に構築しており、無償範囲での利用にトライしているため）、またアプリがMonacaでJSON取得先がGCEの場合に、クロスドメイン制約に引っかかるだろう、など乗り越えるべき壁はまだまだありそうです・・・

## 浮気

もうダメだと思って、ちょっと浮気も考えました。クロスプラットフォーム開発の基盤として、まずUnity。  
ゲーム以外にでも使えるだろうとは思うのですが、はてさて。。。  
次に考えたのはXamarin。iOS用のビルドにMac端末が必要とのことで、もうしばらく様子見。  
浮気せずにすんだのは、良かったのかな・・・

&nbsp;

<div class="kaerebalink-box" style="text-align: left; overflow: hidden; padding-bottom: 20px; font-size: small; -ms-zoom: 1;">
  <div class="kaerebalink-image" style="margin: 0px 15px 10px 0px; float: left;">
    <a href="https://www.amazon.co.jp/exec/obidos/ASIN/B07CQLGGP9/jqinglong-22/" target="_blank" rel="noopener"><img style="border: currentcolor;" src="https://i2.wp.com/images-fe.ssl-images-amazon.com/images/I/51tduFt4DxL._SL160_.jpg?ssl=1" data-recalc-dims="1" /></a>
  </div>
  
  <div class="kaerebalink-info" style="line-height: 120%; overflow: hidden; -ms-zoom: 1;">
    <div class="kaerebalink-name" style="line-height: 120%; margin-bottom: 10px;">
      <p>
        <a href="https://www.amazon.co.jp/exec/obidos/ASIN/B07CQLGGP9/jqinglong-22/" target="_blank" rel="noopener">速習webpack 速習シリーズ</a>
      </p>
      <div class="kaerebalink-powered-date" style="line-height: 120%; font-family: verdana; font-size: 8pt; margin-top: 5px;">
        posted with <a href="https://kaereba.com" target="_blank" rel="nofollow noopener">カエレバ</a>
      </div>
    </div>
    <div class="kaerebalink-detail" style="margin-bottom: 5px;">
      山田祥寛 WINGSプロジェクト 2018-04-27
    </div>
    <div class="kaerebalink-link1" style="margin-top: 10px;">
    </div>
  </div>
</div>

<div class="booklink-footer" style="clear: left;">
  <h4>
    関連記事
  </h4>
  
  <ul>
    <li>
      <a title="VSUG DAY 2013 Summer" href="https://www.programmers-office.ml/2013/07/20/vsug-day-2013-summer/" rel="bookmark">VSUG DAY 2013 Summer</a>
    </li>
    <li>
      <a title="とりあえずxamarinチュートリアル中（初心者の超入門編）" href="https://www.programmers-office.ml/2018/10/13/%e3%81%a8%e3%82%8a%e3%81%82%e3%81%88%e3%81%9axamarin%e3%83%81%e3%83%a5%e3%83%bc%e3%83%88%e3%83%aa%e3%82%a2%e3%83%ab%e4%b8%ad%ef%bc%88%e5%88%9d%e5%bf%83%e8%80%85%e3%81%ae%e8%b6%85%e5%85%a5%e9%96%80/" rel="bookmark">とりあえずxamarinチュートリアル中（初心者の超入門編）</a>
    </li>
  </ul>
</div>