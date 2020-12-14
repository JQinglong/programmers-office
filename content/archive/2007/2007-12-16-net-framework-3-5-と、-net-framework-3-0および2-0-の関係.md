---
title: .NET Framework 3.5 と、.NET Framework 3.0および2.0 の関係
type: post
date: 2007-12-16T05:16:26+00:00
archives:
    - 2007
url: /net-framework-3-5-と、-net-framework-3-0および2-0-の関係/
post_views_count:
  - 112

---
先日の<a href="http://vsug.jp/tabid/173/Default.aspx" target="_blank">VSUG Day 2007 Winter</a>で、一番うぉっと思ったのが、この関連の話題。 

<a href="http://blogs.msdn.com/dd_jpn/archive/2007/11/13/6172535.aspx" target="_blank">.NET Framework 3.5 と、.NET Framework 3.0および2.0 の関係</a> 

> &nbsp; そこで、.NET Framework 2.0 以降のフレームワークでは、これまでのバージョンアップで熟成されてきた.NET Framework 2.0 を「核」としてそのまま使うことにし、新機能を持つクラスライブラリを追加する形態になりました。 
> 
> &nbsp; こうすることで、無駄な重複部分がインストールされることを防ぎ、かつ安定した .NET Framework 2.0 の CLRを常に使うことができるようになりました。 
> 
> （※ .NET Framework 3.5 以降のフレームワークの構成については、現在のところ未定です。） 
> 
> &nbsp; そのように、.NET Framework 2.0 に拡張ライブラリをのせてリリースされた最初の .NET Framework が、.NET Framework 3.0でした。 
> 
> &nbsp; .NET Framework 3.0 = .NET Framework 2.0 + WPF + WCF + WF + CS  
> &nbsp; そして今回、・・・（一部略）  
> &nbsp; .NET Framework 3.5 = .NET Framework 3.0 SP1 + DLINQ, AJAX, &#8230; 
> 
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; = (( .NET Framework 2.0 × Update )&nbsp; + WPF + WCF + WF + CS ) × Update + DLINQ, AJAX, &#8230; 

これはある意味合理的なのです（Cドライブどんだけ必要なんだという感じになってきていますし）が、これまでと扱いが違うので、少なくとももっと宣伝はしてほしいと思います。  
すなわち、side-by-sideのおかげで、3.0・3.5をインストールしても、2.0アプリには影響しないから問題なかろうと思っている人は多いのではないかと思うのです。 

下記参照  
<a href="http://msdn2.microsoft.com/ja-jp/library/8477k21c(VS.80).aspx" target="_blank">side-by-side 実行</a>

> side-by-side 実行は、コードの複数のバージョンをインストールし、アプリケーションが共通言語ランタイムまたはコンポーネントのどのバージョンを使用するかを選択できる機能です。それ以降に、ランタイム、アプリケーション、またはコンポーネントの他のバージョンをインストールしても、既にインストールされているアプリケーションは影響を受けません。 

しかし、3.5インストールによって2.0SP1が適用されるとすると、たとえばSP1によって修正されるバグを前提にした記述があったりすると、動作が変わってしまわないとも限らないわけで、そんなに気軽にはやりたくないわけです。  
しかも、自分でインストールするならば何らかの情報表示でSP1が当たることに気づいてそこで注意するかもしれませんが、うっかり他人に「2.0と3.xは別の環境なので気にせずインストールしていいですよ」なんて言ってしまうと、まずそのメッセージを見て再確認をしてくれることは期待できません。 

いや、危なく会社マシンにインストールしようとしてしまったので・・・。  
結局しばらく3.5アプリを動かせないと思うと悲しい・・・。  
それにしても、いつSP1当てたらよいのだろう・・・。