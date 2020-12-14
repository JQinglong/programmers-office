---
title: Visual Studioでタグ付き正規表現による置換
type: post
date: 2005-11-12T04:45:13+00:00
archives:
    - 2005
url: /visual-studioでタグ付き正規表現による置換/
post_views_count:
  - 1267

---
先日の[NUnitとJUnitの件][1]の続きです。  
Visual Studioで正規表現を使った置換ができるのはヘルプを見れば分かるのですが、慣れていないとなかなか使えないですね。  
<http://www.microsoft.com/japan/msdn/library/default.asp?url=/japan/msdn/library/ja/vsintro7/html/vxgrfregularexpressionss.asp>  
例えば、次のような置換をしたい場合、  
assertEquals(&#8220;3&#8221;, emp.getDeptno(), dept.getDeptno());  
↓  
Assert.AreEqual(emp.getDeptno(), dept.getDeptno(), &#8220;3&#8221;);  
タグ付き正規表現を使います。  
検索する文字列：  
assertEquals\({\&#8221;[1-9]\&#8221;}, {.*}\)\;  
置換後の文字列：  
Assert.AreEqual(\2, \1);  
「条件」をチェックして正規表現を選択して置換すると、見事にやってくれます。  
やった！  
{}で囲むと、そこにはタグが付いたことになり、\1～9で使うことができるという仕組みです。

 [1]: http://konnokiyotaka.txt-nifty.com/pgblog/2005/10/nunitjunit_e315.html