---
title: Enterprise Library　ファーストインプレッション
type: post
date: 2005-07-24T04:17:00+00:00
url: /enterprise-library　ファーストインプレッション/
post_views_count:
  - 1089

---
[patterns & practices Enterprise Library][1]や、最近の[@ITの市川さんの記事][2]に大いに影響を受けて、Enterprise Libraryをずっと触ってみたかったのですが、やっとちょっとだけ見てみる時間ができました。  
バージョンは、[1.1（June 2005）][3]です。  
で、まずは@ITでも最初に取り上げられている、Data Access Application Block（DAAB）から見てみたわけですが、こういうのはやはり自分でラッパーは用意すべきなのでしょうね。  
私のイメージでは、Datasetの取得は  
ds = db.GetDS(tbl,sql)  
てな感じでやりたいのですが、DAABはそこまで提供はしてくれていません。しかも、おそらく一番手軽なDataset取得メソッドであるExecuteDataSetメソッドは、その中のテーブル名が&#8221;Table&#8221;という固定文字で書かれているので、取得したあと使う側はそれを認識していないといけないわけです。  
なので、ラッパーとして  
&nbsp;&nbsp;&nbsp;&nbsp;Public Const TBLName As String = &#8220;Table&#8221;  
&nbsp;&nbsp;&nbsp;&nbsp;Public Function GetDS(ByRef sql As String) As DataSet  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Dim db As Database = DatabaseFactory.CreateDatabase()  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Dim dbCommandWrapper As DBCommandWrapper = db.GetSqlStringCommandWrapper(sql)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Return db.ExecuteDataSet(dbCommandWrapper)  
&nbsp;&nbsp;&nbsp;&nbsp;End Function  
みたいな感じのものがあるとよいなと思ったわけです。この場合は使う側は  
&nbsp;&nbsp;&nbsp;&nbsp;ds = xx.GetDS(sql)  
&nbsp;&nbsp;&nbsp;&nbsp;ds.Tables(xx.TBLName).DefaultView.Sort = xxx  
みたいな感じになります。  
しかし、もう少し探してみると、  
&nbsp;&nbsp;&nbsp;&nbsp;public virtual void LoadDataSet(DBCommandWrapper command, DataSet dataSet, string tableName)  
なんてものが用意されていました。これを使うと、ラッパーの中身は  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Dim ds As New DataSet  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Call db.LoadDataSet(dbCommandWrapper, ds, Me.TBLName)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Return ds  
となります。この方が、何かとよい気がしますが。使い分け必要かな・・・。  
で、.NET2.0環境では、まだ動かせません。構成ファイルの書き方が違うような、別の場所のような・・・もう少し調べてみましょう。

 [1]: http://enterpriselibrary.jp/
 [2]: http://www.atmarkit.co.jp/fdotnet/entlib/index/index.html
 [3]: http://msdn.microsoft.com/practices/default.aspx?pull=/library/en-us/dnpag2/html/entlib.asp