---
title: Atlas March 2006 CTP
type: post
date: 2006-03-25T05:04:33+00:00
url: /atlas-march-2006-ctp/
post_views_count:
  - 232

---
エバンジェリストグループ Blogにて、最新CTP や、それにまつわる情報がアナウンスされています。  
<http://www.exconn.net/Blogs/team03/archive/2006/03/21/8115.aspx>  
その中で、コミュニティサイト  
<http://atlas.asp.net/>  
が紹介されていますが、そのビデオを見るとまた驚いてしまいます（「Download this video」からどうぞ）。  
イメージとしては、atlasタグで囲んであげればOK、みたいな感じ。  
本当に？というわけで早速インストール。今回はC#だけでなくVBも提供されています。あえて、前バージョンをアンインストールせずやってみましたが、上書き確認が出ますので上書き。  
合わせて、Sample Applicationもインストールします。  
何はともあれ、サンプルを見てみようということで、ファイル > Webサイトを開く > C:\Program Files\Microsoft ASP.NET\Atlas Sample Applications\TaskList。  
これでビルドすると失敗するので、Microsoft.Web.Atlas.dllへの参照を追加します。  
さらに接続文字列も確認しておきます。ASPNETDB.MDFと書いてありますが、TaskListの中にはありませんので、Atlas Sample Applications\Contacts\App_Dataからコピーします（笑　いいのか？？）。  
で、ログインして操作してみたのがこんな感じです。  
<a href="https://i2.wp.com/jqinglong.html.xdomain.jp/bimg/TaskList.jpg" onclick="window.open(this.href, '_blank', 'width=908,height=396,scrollbars=no,resizable=no,toolbar=no,directories=no,location=no,menubar=no,status=no,left=0,top=0'); return false"><img alt="TaskList" title="TaskList" src="https://i0.wp.com/jqinglong.html.xdomain.jp/bimg/TaskList_thumb.jpg?resize=100%2C43" width="100" height="43" border="0"  data-recalc-dims="1" /></a>  
ただ、重大な問題が！全然Ajaxじゃない！！普通にポストバックしてるし！  
と思ったら、これじゃなくて、↓こいつらを動かしてあげないといけないんですね。  
こいつらは、ちゃんとAtlasしてました。  
<a href="https://i1.wp.com/jqinglong.html.xdomain.jp/bimg/SolutionExpl.jpg" onclick="window.open(this.href, '_blank', 'width=225,height=101,scrollbars=no,resizable=no,toolbar=no,directories=no,location=no,menubar=no,status=no,left=0,top=0'); return false"><img alt="SolutionExpl" title="SolutionExpl" src="https://i2.wp.com/jqinglong.html.xdomain.jp/bimg/SolutionExpl_thumb.jpg?resize=100%2C44" width="100" height="44" border="0"  data-recalc-dims="1" /></a>  
<a href="https://i0.wp.com/jqinglong.html.xdomain.jp/bimg/List.jpg" onclick="window.open(this.href, '_blank', 'width=914,height=358,scrollbars=no,resizable=no,toolbar=no,directories=no,location=no,menubar=no,status=no,left=0,top=0'); return false"><img alt="List" title="List" src="https://i0.wp.com/jqinglong.html.xdomain.jp/bimg/List_thumb.jpg?resize=100%2C39" width="100" height="39" border="0"  data-recalc-dims="1" /></a>  
<a href="https://i1.wp.com/jqinglong.html.xdomain.jp/bimg/panel.jpg" onclick="window.open(this.href, '_blank', 'width=909,height=422,scrollbars=no,resizable=no,toolbar=no,directories=no,location=no,menubar=no,status=no,left=0,top=0'); return false"><img alt="panel" title="panel" src="https://i1.wp.com/jqinglong.html.xdomain.jp/bimg/panel_thumb.jpg?resize=100%2C46" width="100" height="46" border="0"  data-recalc-dims="1" /></a>  
ちょうど、趣味のアプリにToDoリストを付けたかったので、組み込んでみたいと思います。