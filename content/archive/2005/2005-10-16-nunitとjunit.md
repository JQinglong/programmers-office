---
title: NUnitとJUnit
type: post
date: 2005-10-16T12:33:02+00:00
archives:
    - 2005
url: /nunitとjunit/
post_views_count:
  - 782

---
今日は一日JUnit用のテストコードをNUnit用に書き換えていたのですが、どうしてAssertの書き方を変えてしまっているのでしょうね。  
NUnit  
Assert.AreEqual( object expected, object actual, string message );  
JUnit  
assertEquals(java.lang.String message, java.lang.Object expected, java.lang.Object actual)  
メソッド名等の違いは置換すればよいですが（一発置換用のVisualStudioマクロを作りながらやっていましたが、次のファイルから効果がでるとよいな～）、メッセージの位置が違うのは痛い・・・  
よい方法ないものでしょうか？？明日も試行錯誤は続く・・・