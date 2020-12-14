---
title: 'Code4StartUp ～ UberEatsを作ろう ～ Sign In & Sign Out'
author: KONNO Kiyotaka
type: post
date: 2018-05-26T00:19:17+00:00
archives:
    - 2018
url: /code4startup-～-ubereatsを作ろう-～-sign-in-sign-out/
post_views_count:
  - 1075
categories:
  - プログラミング
tags:
  - Code4Startup

---
<a href="https://code4startup.com/?ref=kiyotakakonno" target="_blank" rel="noopener">Code4Startup</a>

画面を横に並べて、動画見ながらコーディング、という形にすればよいのでしょうが、動画を見てから書こうとすると、しばしば間違いが。

ログインページのテンプレートファイルで  
{% load staticfiles %}  
を忘れずに。忘れるとinvalid block tag &#8216;static&#8217;というエラーが発生。

{% csrf_token %}  
というお約束。こういうの見ると萌える。

で、一通り書いてみましたが、  
http://（公開アドレス）:8000/restaurant/sign-in/  
で何も表示されない。なんだろうと探ります。

あまりコーディング中の自動補完（clodu9のAce Editor）は正しくないのも、うーん（Visual Studioっ子なので）。  
django.contrib.auth のauthが表示されなかったり、  
auth\_views.logoutは表示されるけど、auth\_views.loginは表示されなかったり。

かなり手間取りましたが、実際は単なる記述ミス。  
<form>タグは自動補完が走り、例えば<formでタブを打っても閉じタグまで書いてくれる。  
そこで変に「>」を入力すると「</form>>」になってしまう罠。

ちなみに、url名は「sign-in」、テンプレート名は「sign_in.html」みたいなのは、一般ルールでしょうか？  
これもsign-inと書くべきところをsign_inと書いていたりしました（そういう補完候補が出る、というのもあるし）。

なんとかかんとか、ログイン認証の仕組みができました。先は長いぞ。

<a href="https://code4startup.com/?ref=kiyotakakonno" target="_blank" rel="noopener">Code4Startup</a>

&nbsp;

<div class="kaerebalink-box">
  <div class="kaerebalink-image">
    <a href="https://www.amazon.co.jp/exec/obidos/ASIN/4873117585/jqinglong-22/" target="_blank" rel="noopener"><img style="border: currentcolor;" src="https://i1.wp.com/images-fe.ssl-images-amazon.com/images/I/512ru2i5gyL._SL160_.jpg?ssl=1" data-recalc-dims="1" /></a>
  </div>
  
  <div class="kaerebalink-info">
    <div class="kaerebalink-name">
      <a href="https://www.amazon.co.jp/exec/obidos/ASIN/4873117585/jqinglong-22/" target="_blank" rel="noopener">ゼロから作るDeep Learning ―Pythonで学ぶディープラーニングの理論と実装</a>
    </div>
    <div class="kaerebalink-powered-date">
      posted with <a href="https://kaereba.com" target="_blank" rel="nofollow noopener">カエレバ</a>
    </div>
    <div class="kaerebalink-detail">
      斎藤 康毅 オライリージャパン 2016-09-24
    </div>
    <div class="kaerebalink-rank">
      <div class="kaerebalink-salesranking" style="margin-bottom: 5px;">
        売り上げランキング : 231
      </div>
    </div>
  </div>
  
  <div class="kaerebalink-footer">
  </div>
  
  <div class="kaerebalink-footer" style="clear: left;">
  </div>
</div>