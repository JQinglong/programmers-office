---
title: App Engine でのモデル定義
type: post
date: 2008-06-29T16:10:33+00:00
url: /app-engine-でのモデル定義/
post_views_count:
  - 81

---
Google App Engineでは、データストアとして、よくあるDBではなく独自のDBを使い、テーブル定義をしなくても、db.Modelというクラスを作れば、簡単にデータを保存できます。  
[http://code.google.com/intl/ja/appengine/docs/datastore/overview.html][1]

で、確かに、ちょっとしたものを作る分にはそれでよいと思うのですが、きっと中の人は何かツール使ってると思うんですよね。データ定義がコード内にしかないのは、ちょっとどうよと思うわけです。その辺のテーブルデザインツールが使えないというのもちょっとなと。例えば、カラム（App Engine的にはプロパティ）の型に何が使えるかを、リファレンスを見ないと分からないわけです。

ということで、App EngineとPythonの練習を兼ねて、ちょっとしたツールを。

[http://klabs.appspot.com/][2]

全ての型を入れていないし、順番入れ替えも、そもそも削除もできないってどういうことよ、ってな感じですが、これから遊びながらいろいろ付け足したいと思います。

<a href="http://www.accesstrade.net/at/c.html?rk=01000pw00044mz" target="_blank"><img alt="月額２６３円からのレンタルサーバー！ロリポップ！" src="http://www.accesstrade.net/at/r.html?rk=01000pw00044mz" border="0" /></a>

 [1]: http://code.google.com/intl/ja/appengine/docs/datastore/overview.html "http://code.google.com/intl/ja/appengine/docs/datastore/overview.html"
 [2]: http://klabs.appspot.com/ "http://klabs.appspot.com/"