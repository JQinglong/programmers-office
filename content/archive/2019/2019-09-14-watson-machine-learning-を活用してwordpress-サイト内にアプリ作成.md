---
title: Watson Machine Learning を活用してWordPress サイト内にアプリ作成
author: KONNO Kiyotaka
type: post
date: 2019-09-14T00:34:41+00:00
url: /watson-machine-learning-を活用してwordpress-サイト内にアプリ作成/
featured_image: /wp-content/uploads/2018/11/imac-300x300.jpg
post_views_count:
  - 820
categories:
  - プログラミング
tags:
  - AI
  - OutSystems
  - WordPress

---
いつも悩んで終わっている記事になってしまうのですが、今回は作りきった話。  
ただ、作りきってから解説を書こうと思うと熱が冷めてしまっているというジレンマ・・・

IBMのWatson Studio から利用できる機械学習環境 AutoAI で予測モデルを構築し、それを外部PHPアプリから参照するアプリを作りました。<figure class="wp-block-embed-wordpress wp-block-embed is-type-wp-embed is-provider-jq-apps">

<div class="wp-block-embed__wrapper">
  <blockquote class="wp-embedded-content" data-secret="2WLTy33EnA">
    <a href="https://jqselect.sakura.ne.jp/apps/titanic-entry/">タイタニック　チャレンジ</a>
  </blockquote>
</div></figure> 

以前から作ろうとしていた、タイタニックアプリがやっとできた！ということです。<figure class="wp-block-embed-wordpress wp-block-embed is-type-wp-embed is-provider-programmers-office">

<div class="wp-block-embed__wrapper">
  <blockquote class="wp-embedded-content" data-secret="FZPZIZ4v0F">
    <a href="https://www.programmers-office.ml/%e3%82%bf%e3%82%a4%e3%82%bf%e3%83%8b%e3%83%83%e3%82%af%e3%82%a2%e3%83%97%e3%83%aa%e3%82%92%e4%bd%9c%e3%82%8d%e3%81%86%ef%bc%88nuxt-js-%e9%96%8b%e7%99%ba%e7%92%b0%e5%a2%83%e3%81%ae%e5%9f%ba%e6%9c%ac/">タイタニックアプリを作ろう（Nuxt.js 開発環境の基本）</a>
  </blockquote>
</div></figure> 

## システム構成

基本的には、機械学習を行なったモデルをAPIとして公開し、そのAPIを呼び出すアプリを作る、というぬるさくで学習していた構成です。

<a href="https://norwegian-geek.booth.pm/items/1296418" target="_blank" rel="noreferrer noopener" aria-label=" (opens in a new tab)">https://norwegian-geek.booth.pm/items/1296418</a>

いままでかなり色々な方法を試してきたわけですが、AutoAIを知った事で、ローカルで構築した機械学習環境を公開環境に持っていく、という事を考えなくて良くなったのが大きいです。

まずは、AutoAIがデプロイ機能まで持っていて、これでAPIを公開できます。

これを呼び出すアプリは、WordPressサイトを立てて、その中でPHPアプリを書きました。

## AutoAI によるAPI公開

こちらについては、AutoAIで検索するだけでも色々情報が出てきますし、「AutoAI タイタニック」と検索すれば、まさに今回行なったことをみなさんやられているので、割愛します。

これが無料で公開されているというのがすごいなと思います。

## WordPress 環境内にアプリ構築

UI側をどう作るかがこの記事のメインとなります。

最初は、せっかく勉強したということでOutSystemsでやってみようと思いました。

### OutSystems

まず、ちょっと悩んだのが、あまりにもデータとフォームが結合していて、単なる検索条件を入力するための画面を作りたいのに、フォームのためにはデータが必要という構造。フォームを使わない方法も当然あると思いますが、仮のデータを作成する方法でもできなくはなかったです。

REST API呼び出しについては、ちゃんと仕組みが用意されていて、これは便利。テスト呼び出しもしやすい画面が用意されている。  
それで、呼び出しまではできたのですが、取得したデータの処理がうまくできませんでした。これについては、そもそもAutoAIのJSONの構造が複雑すぎませんか？という気もしています。

### WordPress

昔から思っているのですが、CMSで管理するコンテンツというのは、単にブログ等の文章だけではないはず、CMSはサイト全体のデザインの統一性を実現するために使用するもので、そこには文章だけではなくアプリケーションも含まれるのではないでしょうか。その一例として、問い合わせフォームくらいはCMSの機能に含まれたりもすると思うのですが、もっとがっつりしたアプリもCMS管理配下に乗せてしかるべきではないか、という気がしています。

なぜこれを私がこれを強く思うかというと、私がデザインが苦手だからです。なるべくセンスの良いデザインを使わせていただくために、その枠組みの中でアプリも作りたいと思うのです。

実際それはやったことはあるので、自分のできる範囲に戻ったという感じではあります。

### フォームプラグイン

そう考えた上で、今回最初に、Wordpressのプラグインを使って、フォームを作れないかと思いました。  
色々なプラグインを見ていく中で、使えなくないなと思ったのは、Form Maker by 10Web。<figure class="wp-block-embed-wordpress wp-block-embed is-type-wp-embed is-provider-10-web-build-amp-host-your-wordpress-website">

<div class="wp-block-embed__wrapper">
  <blockquote class="wp-embedded-content" data-secret="VLsWHp3Rx7">
    <a href="https://10web.io/plugins/wordpress-form-maker/">The Most Powerful Drag&Drop WordPress Form Builder</a>
  </blockquote>
</div></figure> 

デザインテーマも用意されていて（Wordpress本体のテーマとは完全独立なのは良い悪いあると思いますが）、きれいなデザインのフォームが作れます。  
また、無料で使えるコントロールが充実しています（他の類似プラグインは有料オプションが多い印象）。

ただし、基本的には、あくまでも入力した内容をデータに保存して、せいぜいメールを飛ばす機能。今回やりたかったのは入力値を外部のAPIに渡すこと。フォーム処理の後外部URL等に転送することはできますが、入力値がPOSTされるわけではないのです。

これについては、もう少し頑張ってみました。  
JavaScriptを追加することができますので、

<pre class="wp-block-code"><code>function send_form(){
     
     var f = document.forms["form6"];
     f.method = "POST";
     f.action = "/apps/titanic-result/"
          f.submit();
     
}</code></pre>

みたいなものを追加し、画面側では標準のSubmitボタンを使わずに、ボタンを追加して、OnClickイベントにsend_form()を記載する、ということをすると、指定したところに入力値をPostすることができるわけです。

しかし、これを採用しなかったのは、上記のform6もマジックナンバーになってしまうし、ポストされる各コントロールの名前も画面に追加した順に決まってしまう、すなわち開発環境と本番環境で一致させるのが難しいということです。  
更に言えば、フォーム定義のエクスポート・インポートのようなこともできない（と見ましたが、どうでしょう？LayoutのソースまるごとコピペでOK？）ということで、若干運用の難しさがあると感じました。

### Bootstrap

そこで、さらに基本に立ち返って、Bootstrapである程度きれいなフォームは作れそうだ、と考えました。であれば、Bootstrap対応のテーマを使おうということで探してみました。意外と多くはないなと感じたのと、最初はHabakiriが扱いやすそうだと思ったのですが、これだとシンプルすぎるかなというのと、最近は更新されていないようでしたので、見送り。  
<a href="https://habakiri.2inc.org/" target="_blank" rel="noreferrer noopener" aria-label=" (opens in a new tab)">https://habakiri.2inc.org/</a>

若干ベタさが気になりつつ、かつ、Bootstrapは３から上げる気がなさそうなのも気になりつつ、Lightningを使用しました。

<a rel="noreferrer noopener" aria-label=" (opens in a new tab)" href="https://lightning.nagoya/ja/" target="_blank">https://lightning.nagoya/ja/</a>

### ページテンプレート

では、Bootstrapを活用した画面をどう作るか。あまりやっている方がいないように思われるのですが、Wordpressのページテンプレートの仕組みを使います。

[https://wpdocs.osdn.jp/%E3%83%9A%E3][1]<a rel="noreferrer noopener" aria-label="% (opens in a new tab)" href="https://wpdocs.osdn.jp/%E3%83%9A%E3%83%BC%E3%82%B8%E3%83%86%E3%83%B3%E3%83%97%E3%83%AC%E3%83%BC%E3%83%88" target="_blank">%</a>[83%BC%E3%82%B8%E3%83%86%E3%83%B3%E3%83%97%E3%83%AC%E3%83%BC%E3%83%88][1]

テーマのカスタマイズにあたるので、子テーマを作って、その中にテンプレート用のPHPファイルを作っていきます。Lightningの場合は、子テーマ用ファイルも提供されているので、それをthemes配下に置いた上で、そこにさらに今回だと、titanic-entry.phpとtitanic-result.phpという二つのファイルを置きました。

それぞれの内容は、全体構成はページテンプレートの作法に従って、テンプレート名を指定したり、ヘッダを読み込むなら<?php get_header(); ?>を書いたりとか（逆に読み込まないで、他のページとの独自性を出すこともできる）した上で、コンテンツ内容としてBootstrap的HTMLを書きます。当然formタグも好きなように書くので、titanic-entryのフォームで、入力内容をtitanic-resultにPOSTするようにします。

ページテンプレートを作成したら、固定ページを作成して、そのページ属性として作成したテンプレートを選択します。テンプレートを指定することにより、その内容が出力されるので、固定ページ自体の内容は何も書かなくて構いません。<figure class="wp-block-image">

<img src="https://i0.wp.com/www.programmers-office.ml/wp-content/uploads/2019/09/スクリーンショット-2019-09-14-9.21.11.png?ssl=1" alt="" class="wp-image-3159" srcset="https://i0.wp.com/www.programmers-office.ml/wp-content/uploads/2019/09/スクリーンショット-2019-09-14-9.21.11.png?w=480&ssl=1 480w, https://i0.wp.com/www.programmers-office.ml/wp-content/uploads/2019/09/スクリーンショット-2019-09-14-9.21.11.png?resize=300%2C196&ssl=1 300w" sizes="(max-width: 480px) 100vw, 480px" data-recalc-dims="1" /> </figure> 

受取側も、POST値を受け取って、APIに投げて、APIからのレスポンスに基づいて、加工する等して（というのをPHPで書いて）、Bootstrap的HTMLを組み立てる、ということになります。

このPHPで各部分がブラックボックスにならないので、自分で分かって書けるし、かつ、Wordpress配下にあることで、Wordpressのフレームワーク（様々な関数が提供されています）を使える、ということで個人的には、綺麗なアーキテクチャだと思います。

## おまけ

やはり、作りながらログ的な内容をここに書いていったほうが良いかなと思いつつ、これより更に踏み込んだまとめ（構成、手順、ソース）をQiitaの方に書けると良いなと思いつつ・・・

 [1]: https://wpdocs.osdn.jp/%E3%83%9A%E3%83%BC%E3%82%B8%E3%83%86%E3%83%B3%E3%83%97%E3%83%AC%E3%83%BC%E3%83%88