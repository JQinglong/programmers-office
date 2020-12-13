---
title: App Engine 開発環境
type: post
date: 2008-05-24T16:01:53+00:00
url: /app-engine-開発環境/
post_views_count:
  - 96

---
まだ招待してもらえませんが、ぼちぼちたくらみ開始。

##### 統合開発環境（IDE）

まずここから。

[PyScripter][1]  
[SPE IDE][2]  
[Pydev][3]  
それぞれの紹介記事として、  
[Python開発統合環境の決定版！][4]  
[Python のスレッドについての資料と Python の統合開発環境 (IDE) &#8211; 傀儡師の館][5]  
[Fomalhaut of Piscis Australis : [ python ] Eclipse に PyDev をインストールする][6]  
など。

ぱっと見は、PyScripterがよいような気がする。きっとRubyにおけるRDE。しかし、ここはあえてPyDevにしてみます。macでもやるかもしれないので（たぶんやらないけど）、Delphiというのがやや残念。

##### Python

<a href="http://www.python.org/" target="_blank">Python</a> は普通に最新の2.5.2

##### Eclipse

PyDevを使うということは、Eclipse。起動してみると3.2でしたが、どうやら世間の皆さんは3.3.xのようです。特に使ってるわけでもないので、前に入れたものを最新版に入れ替えようと思ったのですが、[All-In-One Eclipse][7]は3.2.0ベースとのことで、しかもリンク先の様子がおかしい。ということで、今回は[AmaterasIDE Installer][8]にしてみます。

起動したら、PyDevの設定。  
[Fomalhaut of Piscis Australis : [ python ] Eclipse に PyDev をインストールする][6]  
[ITmedia エンタープライズ：Eclipse＋PyDEV＝Python統合開発環境][9]  
などを参考。

App Engine

さらにApp Engine環境としてSDK。  
[http://code.google.com/appengine/downloads.html][10]

##### 最初の一歩

まずはこちらを参考に、超基本から。  
[http://builder.japan.zdnet.com/sp/google-app-engine/story/0,3800086196,20371257-2,00.htm][11]

と言いつつ、いきなり  
socket.error: (10013, &#8216;Permission denied&#8217;)  
というエラーではまりましたが、IISでポート8080を使ってしまっていたからでした。そちらを止めると無事画面表示ができました。  
ちなみに、下記WARNINGは気にしなくてよいようです。  
WARNING&nbsp; 2008-05-24 13:01:01,667 datastore\_file\_stub.py] Could not read datastore data from c:\users\konno\appdata\local\temp\dev_appserver.datastore  
WARNING&nbsp; 2008-05-24 13:01:01,668 datastore\_file\_stub.py] Could not read datastore data from c:\users\konno\appdata\local\temp\dev_appserver.datastore.history

では、Eclipseでの実行はどうか。以下の二つを合わせ読みながら。  
[http://d.hatena.ne.jp/c9katayama/20080412/1207995411][12]  
[http://www.r-stone.net/blogs/satoshi/labels/PyDev.html][13]  
一個分かりにくかったのが、dev_appserverを起動しなければいけないため、実行の構成を定義しなければいけないわけですが、一回そのまま実行して失敗しないと設定画面が表示されないということでした。  
また、起動するのはあくまでもdev_appserverということで、それらをプロジェクトフォルダにコピーしなくてはいけないというのが、ちょっとダサいなと思っていろいろ試したのですが、ダメでしたので、コピーしてそれを実行するのが無難なようです。

今日はここまで！

&#8212;  
<a href="http://www.accesstrade.net/at/c.html?rk=01001dwx0044mz" target="_blank"><img alt="アクセストレード" src="http://www.accesstrade.net/at/r.html?rk=01001dwx0044mz" border="0" /></a>

 [1]: http://groups.google.com/group/PyScripter
 [2]: http://pythonide.stani.be/
 [3]: http://pydev.sourceforge.net/index.html
 [4]: http://python.matrix.jp/apps/pyscripter.html
 [5]: http://plaza.rakuten.co.jp/kugutsushi/diary/200710290000/
 [6]: http://foma-zakki.cocolog-nifty.com/zakki/2006/12/_python_eclipse_2739.html
 [7]: http://aioec.sourceforge.jp
 [8]: http://amateras.sourceforge.jp/cgi-bin/fswiki/wiki.cgi?page=AmaterasIDEInstaller
 [9]: http://www.itmedia.co.jp/enterprise/articles/0702/08/news015.html
 [10]: http://code.google.com/appengine/downloads.html "http://code.google.com/appengine/downloads.html"
 [11]: http://builder.japan.zdnet.com/sp/google-app-engine/story/0,3800086196,20371257-2,00.htm "http://builder.japan.zdnet.com/sp/google-app-engine/story/0,3800086196,20371257-2,00.htm"
 [12]: http://d.hatena.ne.jp/c9katayama/20080412/1207995411 "http://d.hatena.ne.jp/c9katayama/20080412/1207995411"
 [13]: http://www.r-stone.net/blogs/satoshi/labels/PyDev.html "http://www.r-stone.net/blogs/satoshi/labels/PyDev.html"