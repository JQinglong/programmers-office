---
title: Atlas Wiki いじり中
type: post
date: 2006-03-19T17:07:35+00:00
url: /atlas-wiki-いじり中/
post_views_count:
  - 587

---
ASP.NET &#8220;Atlas&#8221; Wiki  
<http://msdn.microsoft.com/asp.net/info/future/atlas_wiki/>  
vsiファイルからのインストールはウィザードに従うのみ。  
インストール後に、VS2005でファイル > 新しいWebサイト をやると、下のように、テンプレートが追加されていることが分かります。  
<a href="https://i1.wp.com/jqinglong.html.xdomain.jp/bimg/template.jpg" onclick="window.open(this.href, '_blank', 'width=794,height=418,scrollbars=no,resizable=no,toolbar=no,directories=no,location=no,menubar=no,status=no,left=0,top=0'); return false"><img alt="template" title="template" src="https://i0.wp.com/jqinglong.html.xdomain.jp/bimg/template_thumb.jpg?resize=100%2C52" width="100" height="52" border="0"  data-recalc-dims="1" /></a>  
これで自動的にサイトを作ってくれます。そしておもむろに実行すると、データベースに接続できませんエラー。  
ここはちょっとはまりました。  
SQL Server 2005 Expressの人は、もしかしたらそのままいけるかもしれません。  
そうでない人は、Web.configの接続文字列を変更します。この時に、自動で立ち上がる開発サーバーポートはいったん終了する必要があるようです。接続文字列の変更が反映していないだけなのに色々いじっても状況が変わらず、悩みました。  
最終的には、こんな感じ。※私は、SQL Server 2005用のインスタンスを「SQL2005」にしています。  
<add name=&#8221;defaultSqlServer&#8221; connectionString=&#8221;Data Source=(local)\SQL2005;Integrated Security=True;AttachDBFilename=|DataDirectory|AtlasWiki.mdf&#8221; />  
そうすると、下のようなページが出てきます。おしゃれ～  
<a href="https://i1.wp.com/jqinglong.html.xdomain.jp/bimg/home.jpg" onclick="window.open(this.href, '_blank', 'width=1023,height=797,scrollbars=no,resizable=no,toolbar=no,directories=no,location=no,menubar=no,status=no,left=0,top=0'); return false"><img alt="home" title="home" src="https://i0.wp.com/jqinglong.html.xdomain.jp/bimg/home_thumb.jpg?resize=100%2C77" width="100" height="77" border="0"  data-recalc-dims="1" /></a>  
<a href="https://i1.wp.com/jqinglong.html.xdomain.jp/bimg/contents.jpg" onclick="window.open(this.href, '_blank', 'width=1023,height=797,scrollbars=no,resizable=no,toolbar=no,directories=no,location=no,menubar=no,status=no,left=0,top=0'); return false"><img alt="contents" title="contents" src="https://i0.wp.com/jqinglong.html.xdomain.jp/bimg/contents_thumb.jpg?resize=100%2C77" width="100" height="77" border="0"  data-recalc-dims="1" /></a>  
ログイン  
<a href="https://i1.wp.com/jqinglong.html.xdomain.jp/bimg/login.jpg" onclick="window.open(this.href, '_blank', 'width=1023,height=797,scrollbars=no,resizable=no,toolbar=no,directories=no,location=no,menubar=no,status=no,left=0,top=0'); return false"><img alt="login" title="login" src="https://i0.wp.com/jqinglong.html.xdomain.jp/bimg/login_thumb.jpg?resize=100%2C77" width="100" height="77" border="0"  data-recalc-dims="1" /></a>  
<a href="https://i2.wp.com/jqinglong.html.xdomain.jp/bimg/register.jpg" onclick="window.open(this.href, '_blank', 'width=1023,height=797,scrollbars=no,resizable=no,toolbar=no,directories=no,location=no,menubar=no,status=no,left=0,top=0'); return false"><img alt="register" title="register" src="https://i1.wp.com/jqinglong.html.xdomain.jp/bimg/register_thumb.jpg?resize=100%2C77" width="100" height="77" border="0"  data-recalc-dims="1" /></a>  
検索機能を有効にするには、DBの設定が必要です。SQL Server 2005 Expressではダメみたい。  
<a href="https://i2.wp.com/jqinglong.html.xdomain.jp/bimg/search.jpg" onclick="window.open(this.href, '_blank', 'width=1023,height=797,scrollbars=no,resizable=no,toolbar=no,directories=no,location=no,menubar=no,status=no,left=0,top=0'); return false"><img alt="search" title="search" src="https://i2.wp.com/jqinglong.html.xdomain.jp/bimg/search_thumb.jpg?resize=100%2C77" width="100" height="77" border="0"  data-recalc-dims="1" /></a>  
さて、これでページにコメントを付けようとしたりすると、権限がないと言われます。  
<a href="https://i0.wp.com/jqinglong.html.xdomain.jp/bimg/comments.jpg" onclick="window.open(this.href, '_blank', 'width=1023,height=797,scrollbars=no,resizable=no,toolbar=no,directories=no,location=no,menubar=no,status=no,left=0,top=0'); return false"><img alt="comments" title="comments" src="https://i0.wp.com/jqinglong.html.xdomain.jp/bimg/comments_thumb.jpg?resize=100%2C77" width="100" height="77" border="0"  data-recalc-dims="1" /></a>  
ユーザの登録は「Register」からできるのですが、権限なんてありませんでした。  
で、権限はどこで管理するかというと、VSに戻って、Webサイト > ASP.NET構成 から。  
で、これまたエラーになったので、続きは明日！