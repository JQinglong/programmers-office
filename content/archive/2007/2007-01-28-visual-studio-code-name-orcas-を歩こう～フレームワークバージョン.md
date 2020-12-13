---
title: Visual Studio Code Name "Orcas" を歩こう～フレームワークバージョン指定
type: post
date: 2007-01-28T13:52:34+00:00
url: /visual-studio-code-name-orcas-を歩こう～フレームワークバージョン/
post_views_count:
  - 84

---
ちょっとずつ歩きます。

起動すると、今回もこんな感じでスタートページの左側にガイドが出るので、「What&#8217;s New in Visual Studio Code Name &#8220;Orcas&#8221; Community Technology Previews」を見てみます。  
&nbsp;<a href="https://i1.wp.com/jqinglong.html.xdomain.jp/bimg/VisualStudioCodeNameOrcas_141AC/image%7B0%7D%5B3%5D.png" atomicselection="true"><img style="border-right: 0px; border-top: 0px; border-left: 0px; border-bottom: 0px" height="138" src="https://i0.wp.com/jqinglong.html.xdomain.jp/bimg/VisualStudioCodeNameOrcas_141AC/image%7B0%7D%5B2%5D.png?resize=240%2C138" width="240" border="0" data-recalc-dims="1" /></a>  
が、3点だけ？？  
・Target a Specific .NET Framework for Projects (Multi-Targeting)  
・LINQ  
・Use Testing Features in Visual Studio Professional Edition  
そっけないですね。本当の強化点はこちら。  
[Microsoft Pre-release Software Visual Studio Code Name &#8220;Orcas&#8221; &#8211; January 2007 Community Technology Preview (CTP)][1]

最初は簡単に、フレームワークバージョン指定について。

これまでは、各フレームワークバージョンに対応するVisualStudioが提供されると言う形だったわけですが（例えば、VS2005では2.0の開発のみ可能）、今回は2.0・3.0・3.5のいずれもターゲットとして指定できると言うことです。なお、明記はされていませんが、1.1ソリューションを開こうとしたら変換ウィザードが起動したので、2.0以降に限定されるようです。2.0プロジェクトは確かにそのまま開けました。

で、説明では新規プロジェクト作成時もターゲットバージョンを指定できるように書いてあるのですが、現時点では見つかりません。これはまだでしょうかね。  
<a href="https://i0.wp.com/jqinglong.html.xdomain.jp/bimg/VisualStudioCodeNameOrcas_141AC/image%7B0%7D%5B5%5D.png" atomicselection="true"><img style="border-right: 0px; border-top: 0px; border-left: 0px; border-bottom: 0px" height="201" src="https://i0.wp.com/jqinglong.html.xdomain.jp/bimg/VisualStudioCodeNameOrcas_141AC/image%7B0%7D%5B4%5D.png?resize=240%2C201" width="240" border="0" data-recalc-dims="1" /></a> 

VSを何個もインストールしなくて良くなるのは、意外とうれしいのではないでしょうか。まあ、いまだに1.0の修正も必要なくらいですから、しばらくは1個ですむようにはならないのですが・・・。

 [1]: http://www.microsoft.com/info.aspx?na=47&p=1&SrcDisplayLang=en&SrcCategoryId=&SrcFamilyId=82243606-D16D-445C-8949-9EE8C10CDA2E&u=details.aspx%3ffamilyid%3d1FF0B35D-0C4A-40B4-915A-5331E11C39E6%26displaylang%3den