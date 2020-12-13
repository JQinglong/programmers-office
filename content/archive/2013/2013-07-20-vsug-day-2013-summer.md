---
title: VSUG DAY 2013 Summer
type: post
date: 2013-07-20T14:05:54+00:00
url: /vsug-day-2013-summer/
post_views_count:
  - 192
categories:
  - 未分類
tags:
  - Xamarin

---
参加してきました。  
<http://vsug.jp/tabid/228/EventID/23/Default.aspx>  
しびれました。

### 「Web アプリケーション開発におけるテストの実践」

この分野は進んでいるような、進んでいないような。

進んでいる一つとして、Fakes アセンブリというものを挙げられるかもしれません。  
<http://msdn.microsoft.com/ja-jp/library/vstudio/hh549175.aspx>  
存在も知りませんでしたよ・・・  
ただ、これは、そもそも、方式設計的なところの話で、外部ライブラリをラッパを噛まさずに使うのか、という問題があります。  
例がDateTime.Nowだからイマイチなのかもしれませんが。

コード化された UI テスト  
<http://msdn.microsoft.com/ja-jp/library/vstudio/dd286726.aspx#verifyingcodeusingcuitcreate>  
も、動きはえぐいけど、昔もあったことはあったんですよね。  
名前忘れちゃいました。Rational製品。

結局、面倒くささに勝てるほどにはなっていないのかな。  
イメージとしては、カバレッジを取ってくれるのではなくて、100%にしてくれるテストを生成してくれという感じです。

### 「Xamarin で初めてのクロスプラットフォーム開発」

これも初耳。monoがこのようになっていたとは。  
むしろ、In App Purchaseという、こちらも初耳でしたが、後のセッションにも出てきますが、この辺の業務アプリにはない部分に興味を惹かれました。  
iPohneアプリも、泥臭いんですね。なかなか。

### 「初めての Windows ストア アプリ開発」

しびれ度2.5。  
Windows ストア アプリのデザイン方法は、素直に面白かったです。  
ゲームを作って、ハイスコアの仕組みを作るために、リソースをどう管理するか。まさかの事件勃発も、場合によっては深刻ですが、今回は笑える内容でよかったです。  
こちらでも話題に出てくる課金の仕組み。  
課金状態をどうテストするか、ぱっと聞かれたら分からないですよね。  
<http://blogs.msdn.com/b/windowsstore_ja/archive/2012/07/26/windows-making-money.aspx>  
ちゃんと、CurrentAppSimulator という仕組みが用意されています。  
これはちょっと作ってみたくなりました。その前に、Surface 買っちゃうか、みたいな。買いませんけど。

小ネタとして、多言語アプリ ツールキットはちょっと凄そう。  
<http://msdn.microsoft.com/ja-jp/library/windows/apps/jj569303.aspx>  
絵もないので、分かりにくいですが、多言語用のリソースファイルを管理するだけでなく、翻訳までしてしまう。  
こういうのは、本当に助かる気がします。（もちろん、そのまま使えることは想定しませんが、0からのスタートと10からのスタートは全然違うということです）

もう一つ小ネタとして、Windows アプリ アート ギャラリー、良いと思うのですが、Windows 8 および Windows Phone 用アプリケーションの制作以外への本素材の利用禁止というのは、了見が狭いぞw

### 【SIer と Developer のためのSQL Server 2012 アーキテクチャ】

しびれ度3超！ヘカトン級！！

この資料は会社に置いておきます。絶対使える。  
また、調査用スクリプトも、そのうち公開したいとのことです。下記サイトを、要チェックです。  
<http://www.microsoft.com/ja-jp/sqlserver/2008/r2/technology/takumi.aspx>

2012ってまだ使っていないんですけど、もう2014なんですね。  
[http://technet.microsoft.com/ja-JP/evalcenter/dn205290?WT.mc\_id=Blog\_SQL\_TEE\_SQL2014][1]  
大きな売りが、ヘカトン。ただし、いろいろ制約もあるので使い方は考えなさいと。

NUMAも熱かった。

そして、「BIから入るのではなく、しびれるようなトランザクション系から入って欲しい」この言葉にしびれました。

&#8212;  
やはり、こういう場で刺激を受けることは大切ですね。  
全然ついていけてない、と感じたら、やはりなんとかしたくなりますからね。

何年ぶりかにもかかわらず、トイレで声をかけていただいた福井さん、ありがとうございました。  
次の機会はまた懇親会も参加したいと思います。

 [1]: http://technet.microsoft.com/ja-JP/evalcenter/dn205290?WT.mc_id=Blog_SQL_TEE_SQL2014