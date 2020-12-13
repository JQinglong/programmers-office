---
title: Code4StartUp ～ UberEatsを作ろう ～ Django環境続き
author: KONNO Kiyotaka
type: post
date: 2018-05-04T03:48:48+00:00
url: /code4startup-～-ubereatsを作ろう-～-django環境続き/
post_views_count:
  - 916
categories:
  - プログラミング
tags:
  - Code4Startup

---
Djangoが動作する環境ができたら、アプリを作成していきます。

「python manage.py startapp foodtaskerapp」により  
foodtasker  
foodtaskerapp  
のディレクトリが並ぶ形になります。  
ここから、行ったり来たりになりますが、  
・まずは、foodtaskerのsettings.pyのINSTALLED_APPSに追加  
・次に、foodtaskerappのviews.pyにhomeメソッド追加  
・次に、foodtaskerのurls.pyのurlpatternsに追加  
・次に、foodtaskerappにtemplateディレクトリを作成し、home.html作成

という形で作成していきます。

講義ビデオではatom＋emmetのスニペットが快適そうに見えますが、まあ、そんなに使うものでもないと思うので、Cloud9のAceエディタの機能で進めます。最低限のスニペットはありますので。

いったん実行すると、「TemplateDoesNotExist」エラーが発生しましたが、単純に、  
テンプレートフォルダ名は「template」ではなく「templates」ということでした。失礼。そして、  
python manage.py migrate  
python manage.py createsuperuser  
により、管理画面が表示されます。

bootstrapも組み込んで（Bootstrap 4ではグリフアイコンをサポートしないため、「fonts」フォルダは削除されましたとのことなので、最新版を取得するとここはちょっと違います）、次はTask3です。



<div class="kaerebalink-box">
  <div class="kaerebalink-image">
    <a href="https://www.amazon.co.jp/exec/obidos/ASIN/4873117585/jqinglong-22/" target="_blank"><img style="border: currentcolor; border-image: none;" src="https://i1.wp.com/images-fe.ssl-images-amazon.com/images/I/512ru2i5gyL._SL160_.jpg?ssl=1" data-recalc-dims="1" /></a>
  </div>
  
  <div class="kaerebalink-info">
    <div class="kaerebalink-name">
      <a href="https://www.amazon.co.jp/exec/obidos/ASIN/4873117585/jqinglong-22/" target="_blank">ゼロから作るDeep Learning ―Pythonで学ぶディープラーニングの理論と実装</a>
    </div>
    <div class="kaerebalink-powered-date">
      posted with <a href="http://kaereba.com" target="_blank" rel="nofollow">カエレバ</a>
    </div>
    <div class="kaerebalink-detail">
      斎藤 康毅 オライリージャパン 2016-09-24
    </div>
    <div class="kaerebalink-rank">
      <div class="kaerebalink-salesranking" style="margin-bottom: 5px;">
        売り上げランキング : 303
      </div>
    </div>
  </div>
  
  <div class="kaerebalink-footer">
  </div>
  
  <div class="kaerebalink-footer" style="clear: left;">
  </div>
</div>