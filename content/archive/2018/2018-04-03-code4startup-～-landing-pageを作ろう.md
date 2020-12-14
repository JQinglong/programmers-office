---
title: Code4StartUp ～ Landing Pageを作ろう
author: KONNO Kiyotaka
type: post
date: 2018-04-03T14:44:56+00:00
archives:
    - 2018
url: /code4startup-～-landing-pageを作ろう/
post_views_count:
  - 954
categories:
  - プログラミング
tags:
  - Code4Startup

---
　ちょっと、Noteを使ってみたりもしており、こちらはご無沙汰になりました。  
　Noteのような厳しい制約の中で書くのもそれはそれでありだと思うのですが、ちょっと厳しすぎる感もあり。  
　しかも、有償化はそんな簡単な話ではないなと。  
　ただ、ちゃんと構造化した文書、というものは意識したいなと思います。

### Code4StartUpを始めてみる

　実は結構前に始まっているサービスですが、最近知り、今の私に非常にマッチした学習ができそうということで始めることにしました。  
　登録は無料なのですが、登録すると、時間限定で、プレミアムプロジェクトであるUBER EATSコースが、499ドルから99ドルになるとの表示。あざとい・・・と思いながらぽちりました。なぜならUBER EATSこそが、今回のきっかけだから。

[<img width="244" height="185" title="code4" style="display: inline; background-image: none;" alt="code4" src="https://i2.wp.com/www.programmers-office.ml/wp-content/uploads/2018/04/code4_thumb.png?resize=244%2C185&#038;ssl=1" border="0" data-recalc-dims="1" />][1]

### Landing Page作成プロジェクト

　しかし、最初は無料コースから。  
　無料コースとはいえ、Bootstrapでランディングページを作って公開するところまでやってみよう、というのはなかなかセンスが良いのではと思います。  
　そして、色々知らないサービスも勉強させてもらえました。

**Start Bootstrap**  
<https://startbootstrap.com/>  
　Bootstrapのデザインテンプレート。  
　日本人向けだとまたちょっと違うかなという気もしますが、今回は日本人向けではないので、そういう意味でも役に立ちます。

**Font Awesome**  
<https://fontawesome.com/>  
　講義ビデオの中では、[fontawesome.io][2]になっている。  
　そして、envelope-opeのページに記載されているリンクも、講義ビデオだとclass=&#8221;fa &#8230; だけど、現在のページだとclass&#8221;fas &#8230;  
　理由はFont Awesomeが4から5にアップグレードされているためでした。  
　&#8221;fa fa-map-marker fa-stack-1x fa-inverse&#8221;でアイコンは変更されます。  
　Chromeの右クリックInspectは日本語版だと検証（Ctrl+Shift+I）。  
　講義の中で使われている記述”col-md-offset-3”が反応しない。→offset-md-3が正解。  
　理由はBootstrapが3から4にアップグレードされているため。

**MailChimp**  
<https://mailchimp.com/>  
　メール送信サービス  
。昔DM送信で苦労した記憶が18年たっても忘れられない身としては、ありがたや。

**Wufoo**  
[https://www.wufoo.com/][3]  
　フォーム作成サービス。今どきはこんな風に実装するんですね。

**githubデスクトップ**  
　なかなかgithubを導入しきれませんが、これはちょっと良いかも？後日導入記を書くことになりそう。

**Bluehost**  
　海外有料サーバはあまり調べたことがなかったですが、ここが主力っぽいですね。日本だとさくらの位置づけ。ただ、日本のサービスと違い、1ドメイン取得無料は大きいかも。

一通り見てみました。  
後は、公開前のセキュリティチェック等があるとよいのではと思いました。

そして、UBER EATSコースに入っていきたいと思います。

 [1]: https://i0.wp.com/www.programmers-office.ml/wp-content/uploads/2018/04/code4.png?ssl=1
 [2]: http://fontawesome.io/
 [3]: https://www.wufoo.com/ "https://www.wufoo.com/"