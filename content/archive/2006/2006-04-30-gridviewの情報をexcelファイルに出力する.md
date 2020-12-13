---
title: GridViewの情報をExcelファイルに出力する
type: post
date: 2006-04-29T19:39:17+00:00
url: /gridviewの情報をexcelファイルに出力する/
post_views_count:
  - 900

---
ちょっと前に[どっとねっとふぁんBlogさんで][1]紹介されていたビデオを見て試してみました。  
[Export GridView to Excel (Video)][2]  
簡易Excel出力としてはかなりよいですね。  
TemplateFieldがあると失敗してしまいます（「RegisterForEventValidation は Render(); の実行中にのみ呼び出されることができます。」）が、  
Me.GridView1.Columns(11).Visible = False  
みたいな感じで不可視にすれば逃げられます。  
これについてはVSUGのスレが参考になりました。  
<http://vsug.jp/tabid/63/forumid/47/tpage/1/view/Topic/postid/3056/Default.aspx>  
VSUGバンザイ＼(^o^)／  
おぉ、夜が明けてきた・・・  
GWでみんな片付くとよいな・・・

 [1]: http://dotnetfan.org/blogs/dotnetfanblog/archive/2006/04/20/665.aspx
 [2]: http://gridviewguy.com/ArticleDetails.aspx?articleID=175