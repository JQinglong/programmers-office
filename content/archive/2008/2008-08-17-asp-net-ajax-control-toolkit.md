---
title: ASP.NET AJAX Control Toolkit
type: post
date: 2008-08-17T14:17:27+00:00
archives:
    - 2008
url: /asp-net-ajax-control-toolkit/
post_views_count:
  - 90

---
いまいち情報が充実しないASP.NET AJAX Control Toolkit。PopupControlでややはまり。  
そもそも  
[http://www.asp.net/AJAX/AjaxControlToolkit/Samples/PopupControl/PopupControl.aspx][1]  
を見ても、DynamicControlID、DynamicServiceMethod、DynamicContextKeyの記述がないのはどういうこと？？  
これらを使うと、DynamicContextKeyの値を使用してWebサービスを呼んで、戻り値をDynamicControlIDに指定したコントロールにセットして使用できるという優れもので、明細の中で使うような場合は必須なのですが。

こちら  
[http://aspnet.4guysfromrolla.com/demos/printPage.aspx?path=/articles/071107-1.aspx][2]  
にちょっと助けられましたが、やりながら出たエラーから見るに、DynamicControlIDに実質セットできるのは、Panelだけですかね？？こいつのInnerHtmlに値をセットしようとするようです。本当はテキストボックスのTextにセットして、それを使用してさらに処理したかったのですが、どうしようかな。

<a href="http://www.accesstrade.net/at/c.html?rk=01002eq30044mz" target="_blank"><img alt="" src="http://www.accesstrade.net/at/r.html?rk=01002eq30044mz" border="0" /></a>

 [1]: http://www.asp.net/AJAX/AjaxControlToolkit/Samples/PopupControl/PopupControl.aspx "http://www.asp.net/AJAX/AjaxControlToolkit/Samples/PopupControl/PopupControl.aspx"
 [2]: http://aspnet.4guysfromrolla.com/demos/printPage.aspx?path=/articles/071107-1.aspx "http://aspnet.4guysfromrolla.com/demos/printPage.aspx?path=/articles/071107-1.aspx"