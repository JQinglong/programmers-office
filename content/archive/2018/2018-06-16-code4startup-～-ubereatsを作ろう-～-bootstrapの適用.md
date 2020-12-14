---
title: Code4StartUp ～ UberEatsを作ろう ～ Bootstrapの適用
author: KONNO Kiyotaka
type: post
date: 2018-06-15T23:48:08+00:00
archives:
    - 2018
url: /code4startup-～-ubereatsを作ろう-～-bootstrapの適用/
post_views_count:
  - 915
categories:
  - プログラミング
tags:
  - Code4Startup

---
<a href="https://code4startup.com/?ref=kiyotakakonno" target="_blank" rel="noopener">Code4Startup</a>

以前もstaticの読み込みがうまくいっていなかったのですが、settings.pyを終始して戻して保存したら、style.cssを読んでくれたようです。まだ、完全に同じ見た目にはなっていませんが。もやもや・・・

## Bootstrap4

講義はBootstrap3ベースになっていますが、最新のBootstrap4を使おうとすると、色々調べながら進める必要があります。  
まず、jquery等の読み込みですが、講義で参照しているbasic templateは使用できないので、Introductionを見ると、そこにStarter templateがあります。  
必要なJS読み込みは

> <script src=&#8221;https://code.jquery.com/jquery-3.3.1.slim.min.js&#8221; integrity=&#8221;sha384-q8i/X+965DzO0rT7abK41JStQIAqVgRVzpbzo5smXKp4YfRvH+8abtTE1Pi6jizo&#8221; crossorigin=&#8221;anonymous&#8221;></script>  
> <script src=&#8221;https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.14.3/umd/popper.min.js&#8221; integrity=&#8221;sha384-ZMP7rVo3mIykV+2+9J3UJ46jBk0WLaUAdn689aCwoqbBJiSnjAK/l8WvCWPIPm49&#8243; crossorigin=&#8221;anonymous&#8221;></script>  
> <script src=&#8221;https://stackpath.bootstrapcdn.com/bootstrap/4.1.1/js/bootstrap.min.js&#8221; integrity=&#8221;sha384-smHYKdLADwkXOn1EmN1qk/HfnUcbVRZyYmZ4qpPea6sjB/pTJ0euyQp0Mk8ck+5T&#8221; crossorigin=&#8221;anonymous&#8221;></script>

となっています。

さらに、django-bootstrap3をインストールしていますが、ここはpip install django-bootstrap4にします。

スタイルの読み込みがちゃんとできていないので見た目はもやもやしますが、とりあえず進めます。

<a href="https://code4startup.com/?ref=kiyotakakonno" target="_blank" rel="noopener">Code4Startup</a>

<table style="border: none;" border="0" cellpadding="5">
  <tr>
    <td style="border: none;" valign="top">
      <a href="https://www.amazon.co.jp/exec/obidos/ASIN/4532320186/jqinglong-22/" target="_blank" rel="noopener"><img style="margin-right: 10px;" src="https://i0.wp.com/images-fe.ssl-images-amazon.com/images/I/51OxNhG-s-L._SL160_.jpg?ssl=1" border="0" data-recalc-dims="1" /></a>
    </td>
    <td style="border: none; text-align: left;" valign="top">
      <div class="kaerebalink-name" style="margin-bottom: 10px; line-height: 120%;">
        <a href="https://www.amazon.co.jp/exec/obidos/ASIN/4532320186/jqinglong-22/" target="_blank" rel="noopener">シェアリング・エコノミー　―Uber、Airbnbが変えた世界</a>
      </div>
      <div class="kaerebalink-detail" style="margin-bottom: 5px;">
        宮崎 康二 日本経済新聞出版社 2015-07-23
      </div>
      <div class="kaerebalink-salesranking" style="margin-bottom: 5px;">
        売り上げランキング : 28003
      </div>
      <table style="border: none; margin-top: 10px;">
        <tr>
          <td style="border: none; text-align: left;">
          </td>
          <td style="vertical-align: bottom; padding-left: 10px; font-size: x-small; border: none;">
            by <a href="https://kaereba.com" target="_blank" rel="nofollow noopener">カエレバ</a>
          </td>
        </tr>
      </table>
      <p>
        &nbsp;</td> </tr> </tbody> </table>