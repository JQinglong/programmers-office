---
title: Code4StartUp ～ UberEatsを作ろう ～ Djangoのデバッグ
author: KONNO Kiyotaka
type: post
date: 2018-06-01T07:14:37+00:00
url: /code4startup-～-ubereatsを作ろう-～-djangoのデバッグ/
post_views_count:
  - 953
categories:
  - プログラミング
tags:
  - Code4Startup

---
<a href="https://code4startup.com/?ref=kiyotakakonno" target="_blank">Code4Startup</a>

前回に続き、Registration機能の実装ですが、どうもデータが登録されません。

では、ということでデバッグ実行をしようと思ったのですが、これがまたうまく動きません。

そもそもサービス起動のために  
python manage.py runserver xxx.xxx.xxx.xxx:8000  
を叩かなければいけないということですから、普通にRunボタンを使って実行することができないわけです。  
では、と思って、New Terminalでコマンド実行用のウインドウを開いて、その中で上記のコマンドを叩こうとしましたが、cdコマンドが効いてくれないようです。  
ではでは、  
python foodtasker/manage.py runserver xxx.xxx.xxx.xxx:8000  
とすると、

Traceback (most recent call last):  
&nbsp;&nbsp; File &#8220;foodtasker/manage.py&#8221;, line 17, in <module>  
&nbsp;&nbsp;&nbsp;&nbsp; &#8220;Couldn&#8217;t import Django. Are you sure it&#8217;s installed and &#8220;  
ImportError: Couldn&#8217;t import Django. Are you sure it&#8217;s installed and available on your PYTHONPATH environment variable? Did you forget to activate a virtual environment?  
となってしまいました。

なお、<a href="https://tech-joho.info/aws-cloud9%E3%81%A7python%E9%96%8B%E7%99%BA%E3%81%99%E3%82%8B%E6%BA%96%E5%82%99/" target="_blank">こちらのサイト</a>でも、2017年12月3日現在、デバッグ実行ができないと判断されているようです。

むう。。。

とりあえずはやむを得ないので、<a href="https://qiita.com/NoriakiOshita/items/7716c6e46338768467eb" target="_blank">こちら</a>を参考に、コンソールに出力。いつの時代も安定のコンソール出力。

失敗の原因は色々で、objectsとobject（誤）とか、FalseとFALSE（誤）とか。  
もう少しエディタの力で何とかならないものか・・・

<a href="https://code4startup.com/?ref=kiyotakakonno" target="_blank">Code4Startup</a>



<div class="kaerebalink-box">
  <div class="kaerebalink-image">
    <a href="https://www.amazon.co.jp/exec/obidos/ASIN/4873117585/jqinglong-22/" target="_blank"><img style="border: currentcolor; border-image: none;" src="https://i1.wp.com/images-fe.ssl-images-amazon.com/images/I/512ru2i5gyL._SL160_.jpg?ssl=1" data-recalc-dims="1" /></a>
  </div>
  
  <div class="kaerebalink-info">
    <div class="kaerebalink-name">
      <a href="https://www.amazon.co.jp/exec/obidos/ASIN/4873117585/jqinglong-22/" target="_blank">ゼロから作るDeep Learning ―Pythonで学ぶディープラーニングの理論と実装</a>
    </div>
    <div class="kaerebalink-powered-date">
      posted with <a href="https://kaereba.com" target="_blank" rel="nofollow">カエレバ</a>
    </div>
    <div class="kaerebalink-detail">
      斎藤 康毅 オライリージャパン 2016-09-24
    </div>
    <div class="kaerebalink-rank">
      <div class="kaerebalink-salesranking" style="margin-bottom: 5px;">
        売り上げランキング : 228
      </div>
    </div>
  </div>
  
  <div class="kaerebalink-footer">
  </div>
  
  <div class="kaerebalink-footer" style="clear: left;">
  </div>
</div>