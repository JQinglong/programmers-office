---
title: SQL Server 2005 Express Edition on Vista
type: post
date: 2007-02-11T12:40:28+00:00
archives:
    - 2007
url: /sql-server-2005-express-edition-on-vista/
post_views_count:
  - 87

---
SQL Server 2005 Express Editionを扱うために、Management Studio Expressを使おうと思ったのですが、オプションのネットワークプロトコルが＜既定＞のままだとエラーで落ちてしまいます。こちらの現象ですね。  
[http://forums.microsoft.com/MSDN-JA/ShowPost.aspx?PostID=1162400&SiteID=7][1]  
既定ではSharedMemoryでつなごうとするようで、それではダメなようです。TCP/IPまたはNamed Pipesにすると接続タイムアウトエラーになります。構成の設定は有効にしているつもりですけど。

<a href="https://i2.wp.com/jqinglong.html.xdomain.jp/bimg/SQLServer2005ExpressEditiononVista_11A86/image03_1.png" atomicselection="true"><img style="border-top-width: 0px; border-left-width: 0px; border-bottom-width: 0px; border-right-width: 0px" height="240" src="https://i1.wp.com/jqinglong.html.xdomain.jp/bimg/SQLServer2005ExpressEditiononVista_11A86/image02_1.png?resize=204%2C240" width="204" border="0" data-recalc-dims="1" /></a> 

ちょっと、埒が明かないので、とりあえずVisualStudioのApp_DataからDBを作成することにします。  
で、最初に作ろうとすると、UserInstanceは作れないので、sp_configureを実行してね、と言うようなメッセージが出ます。これまでExpress使っていなかったから意識していなかったんですね。

コマンドプロンプトで  
sqlcmd localhost\sqlexpress  
でログインし  
exec sp_configure &#8216;user instances enabled&#8217;,&#8217;1&#8242;  
go  
とやってやると、DBが作れるようになりました。

（2/21深夜）2/17のSP2では問題なく接続できました！  
<a href="https://i1.wp.com/jqinglong.html.xdomain.jp/bimg/SQLServer2005ExpressEditiononVista_11A86/image%7B0%7D%5B3%5D.png" atomicselection="true"><img style="border-right: 0px; border-top: 0px; border-left: 0px; border-bottom: 0px" height="192" src="https://i2.wp.com/jqinglong.html.xdomain.jp/bimg/SQLServer2005ExpressEditiononVista_11A86/image%7B0%7D%5B2%5D.png?resize=240%2C192" width="240" border="0" data-recalc-dims="1" /></a>

 [1]: http://forums.microsoft.com/MSDN-JA/ShowPost.aspx?PostID=1162400&SiteID=7 "http://forums.microsoft.com/MSDN-JA/ShowPost.aspx?PostID=1162400&SiteID=7"