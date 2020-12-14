---
title: Code4StartUp ～ UberEatsを作ろう ～ heroku環境整備
author: KONNO Kiyotaka
type: post
date: 2018-06-08T01:47:27+00:00
archives:
    - 2018
url: /code4startup-～-ubereatsを作ろう-～-heroku環境整備/
post_views_count:
  - 926
categories:
  - プログラミング
tags:
  - Code4Startup

---
<a href="https://code4startup.com/?ref=kiyotakakonno" target="_blank" rel="noopener">Code4Startup</a>

さて、herokuが動作するようになると、おもむろにGunicornをインストールします。

### Gunicornとは何か

<a href="http://gunicorn.org/" target="_blank" rel="noopener">http://gunicorn.org/</a>  
Gunicorn &#8216;Green Unicorn&#8217; is a Python WSGI HTTP Server for UNIX.  
Python製のWSGI サーバ

### WSGI とは何か

<a href="http://gihyo.jp/dev/feature/01/wsgi/0001" target="_blank" rel="noopener">http://gihyo.jp/dev/feature/01/wsgi/0001</a>  
WSGIはJavaにおけるJava Servelet APIと同じように，WebサーバとWebアプリケーション間の汎用的なインターフェースを定義しています。  
要するに、Djangoを動作させるための土台、と考えればよいでしょうか。  
次にインストールするのが、WhiteNoise

### WhiteNoiseとは何か

<a href="https://pypi.org/project/whitenoise/" target="_blank" rel="noopener">https://pypi.org/project/whitenoise/</a>  
<a href="http://furodrive.com/2016/01/white_noisedjango/" target="_blank" rel="noopener">http://furodrive.com/2016/01/white_noisedjango/</a>  
WhiteNoiseとはWSGIアプリケーションのための静的ファイルを配信するのを簡単にしてくれるライブラリです。  
少しの設定をするだけでAmazon S3やNginxに頼ることなく静的ファイルを配信できます。  
本番サーバーで画像やcss等を参照できるようにするには色々と手順を踏まないといけなかったのですが、WhiteNoiseを使うとそのような手間が省けて大変便利です。  
続いて、dj-database-url

### dj-database-urlとは何か

<a href="https://github.com/kennethreitz/dj-database-url" target="_blank" rel="noopener">https://github.com/kennethreitz/dj-database-url</a>  
<a href="http://y0m0r.hateblo.jp/entry/20121130/1354290868" target="_blank" rel="noopener">http://y0m0r.hateblo.jp/entry/20121130/1354290868</a>  
dj-database-urlを使うとdb接続文字列を環境変数DATABASE_URLから取得させることができます。

### さらにpsycopg2

PythonのPostgreSQL用ドライバ

これで、herokuに乗せるわけですが、色々講義内で想定されているエラー以外に、想定外のエラーが。  
could not determine PostgreSQL version from &#8216;10.4&#8217;  
諸々のサイトを見るとpsycopg2のバージョンを上げろと。  
<a href="http://initd.org/psycopg/docs/" target="_blank" rel="noopener">http://initd.org/psycopg/docs/</a>  
こちらで表示されるのが、現時点で2.7.5なのでそうしてみます。  
そうすると、こんな感じのエラー  
Could not find a version that satisfies the requirement psycopg2==2.7.5 (from -r /tmp/build_f493d80720eb882b01a250f718f3b058/requirements.txt (line 6)) (from versions: 2.0.10, 2.0.11, 2.0.12, 2.0.13, 2.0.14, 2.2.0, 2.2.1, 2.2.2, 2.3.0, 2.3.1, 2.3.2, 2.4, 2.4.1, 2.4.2, 2.4.3, 2.4.4, 2.4.5, 2.4.6, 2.5, 2.5.1, 2.5.2, 2.5.3, 2.5.4, 2.5.5, 2.6, 2.6.1, 2.6.2, 2.7, 2.7.1, 2.7.2, 2.7.3, 2.7.3.1, 2.7.3.2, 2.7.4)  
では2.7.4で。  
できました。It works! Awesome!（この講師の口癖？アメリカ人はよく使う？）

herokuでアプリを起動することもできましたので、  
Task 4: [Python] &#8211; Heroku  
Doneとなります。

<a href="https://code4startup.com/?ref=kiyotakakonno" target="_blank" rel="noopener">Code4Startup</a>

<table style="border: currentcolor;" border="0" cellpadding="5">
  <tr>
    <td style="border: currentcolor;" valign="top">
      <a href="https://www.amazon.co.jp/exec/obidos/ASIN/4822292274/jqinglong-22/" target="_blank" rel="noopener"><img style="margin-right: 10px;" src="https://i0.wp.com/images-fe.ssl-images-amazon.com/images/I/51%2BScGc8DAL._SL160_.jpg?ssl=1" border="0" data-recalc-dims="1" /></a>
    </td>
    <td style="border: currentcolor; text-align: left;" valign="top">
      <div class="kaerebalink-name" style="line-height: 120%; margin-bottom: 10px;">
        <a href="https://www.amazon.co.jp/exec/obidos/ASIN/4822292274/jqinglong-22/" target="_blank" rel="noopener">独学プログラマー Python言語の基本から仕事のやり方まで</a>
      </div>
      <div class="kaerebalink-detail" style="margin-bottom: 5px;">
        コーリー・アルソフ 日経BP社 2018-02-24
      </div>
      <div class="kaerebalink-salesranking" style="margin-bottom: 5px;">
        売り上げランキング : 204
      </div>
      <table style="border: currentcolor; margin-top: 10px;">
        <tr>
          <td style="border: currentcolor; text-align: left;">
          </td>
          <td style="border: currentcolor; padding-left: 10px; font-size: x-small; vertical-align: bottom;">
            by <a href="https://kaereba.com" target="_blank" rel="nofollow noopener">カエレバ</a>
          </td>
        </tr>
      </table>
    </td>
  </tr>
</table>