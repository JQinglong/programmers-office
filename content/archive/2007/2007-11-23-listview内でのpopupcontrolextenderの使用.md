---
title: ListView内でのPopupControlExtenderの使用
type: post
date: 2007-11-23T03:39:21+00:00
url: /listview内でのpopupcontrolextenderの使用/
post_views_count:
  - 132

---
.NET Framework 3.5 で導入されているListViewはいいですよ。 

ところで、その中でASP.NET AJAXのxxExtenderをどう使ったらよいか、ちょっと悩みました。  
結論は簡単で、ItemTemplateの中（とか要は明細の中）に入れてあげればよいということでした。  
同様のことはほかにもあって、同じくASP.NET AJAXのTabPanelの中でExtenderを使う場合もPanelの中に置いてあげるとよいです。 

が、どこかで質問しようと思って質問文まで書いたので、そのまま載せておきます。 

その他の余談として、Visual Studio 2008 RTM 登場に合わせて、ASP.NET AJAX Control Toolkitもアップデートされています。  
<http://www.codeplex.com/AtlasControlToolkit/Release/ProjectReleases.aspx?ReleaseId=8513>  
βで使っていたものは使えないので注意が必要です。一緒にダウンロードしておくべきです。 

というわけで、Let&#8217;s enjoy Visual Studio 2008 ! 

> お世話になります。 
> 
> ListView内の各行でPopupControlExtenderを使用することはできないでしょうか？ 
> 
> 例えば、ListView1のitemtemplateの中にTextBox1を配置し、Load時等に下記処理を行えばできるのではと試してみましたがコントロールが見つからないという下のエラーが発生しました。  
> ItemDataBoundで同様の記述しても同じエラーとなります。  
> もちろん通常通りaspxファイル側で記述しようとしてもエラーになります。 
> 
> 環境は、現在はMicrosoft Visual Studio Team System 2008 Test Edition・AjaxControlToolkit-Framework3.5の11119、その前の2008βでも同様でした。  
> ExtenderはExtender側でTargetControlIDを指定するので、ListViewやGridViewの明細内の項目に適用するのは確かに難しそうですが、うまく使える方法はないでしょうか？ 
> 
> For Each itm As ListViewDataItem In ListView1.Items  
> &nbsp;&nbsp;&nbsp; If itm.ItemType = ListViewItemType.DataItem Then 
> 
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Dim popEx As New AjaxControlToolkit.PopupControlExtender  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Dim tx As TextBox = itm.FindControl(&#8220;TextBox1&#8221;)  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; popEx.TargetControlID = tx.ClientID  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; popEx.PopupControlID = Me.PanelManageTag.ClientID  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; popEx.Position = AjaxControlToolkit.PopupControlPopupPosition.Bottom  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Me.Controls.Add(popEx) 
> 
> &nbsp;&nbsp;&nbsp; End If 
> 
> Next 
> 
> The TargetControlID of &#8221; is not valid. A control with ID &#8216;ctl00\_ContentPlaceHolder1\_ListView1\_ctrl0\_TextBox1&#8217; could not be found. 
> 
> [InvalidOperationException: The TargetControlID of &#8221; is not valid. A control with ID &#8216;ctl00\_ContentPlaceHolder1\_ListView1\_ctrl0\_TextBox1&#8217; could not be found.]  
> &nbsp;&nbsp; System.Web.UI.ExtenderControl.RegisterWithScriptManager() +366  
> &nbsp;&nbsp; System.Web.UI.ExtenderControl.OnPreRender(EventArgs e) +36  
> &nbsp;&nbsp; AjaxControlToolkit.ExtenderControlBase.OnPreRender(EventArgs e) in C:\Users\&#8230;  
> &nbsp;&nbsp; AjaxControlToolkit.PopupControlExtender.OnPreRender(EventArgs e) in C:\Users\&#8230;  
> &nbsp;&nbsp; System.Web.UI.Control.PreRenderRecursiveInternal() +174  
> &nbsp;&nbsp; System.Web.UI.Control.PreRenderRecursiveInternal() +259  
> &nbsp;&nbsp; System.Web.UI.Page.ProcessRequestMain(Boolean includeStagesBeforeAsyncPoint, Boolean includeStagesAfterAsyncPoint) +4483