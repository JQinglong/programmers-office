---
title: OutSystems でのアプリ自動生成
author: KONNO Kiyotaka
type: post
date: 2019-07-17T13:44:52+00:00
url: /outsystems-でのアプリ自動生成/
featured_image: /wp-content/uploads/2018/11/imac-300x300.jpg
post_views_count:
  - 746
categories:
  - プログラミング
tags:
  - Glide App
  - OutSystems

---
一連の投稿の続きになります。

OutSystemsはローコード開発か。ノーコーディングにはならないのか、ということで、OutSystems とGlide App（glideapps）の比較用に、Glide で使用したものと同じデータを使用して、OutSystems でアプリ自動生成を行ってみます。

使用するデータは、下記で調整を行なった、港区観光施設データです。<figure class="wp-block-embed-wordpress wp-block-embed is-type-wp-embed is-provider-programmers-office">

<div class="wp-block-embed__wrapper">
  <blockquote class="wp-embedded-content" data-secret="3DKG1Mtnys">
    <a href="https://www.programmers-office.ml/glide%e3%81%ae%e5%91%b3%e3%82%8f%e3%81%84%e6%96%b9%e3%80%9c%e3%82%aa%e3%83%bc%e3%83%97%e3%83%b3%e3%83%87%e3%83%bc%e3%82%bf%e3%82%92%e6%b4%bb%e7%94%a8%e3%81%97%e3%82%88%e3%81%86/">Glideの味わい方〜オープンデータを活用しよう</a>
  </blockquote>
</div></figure> 

## OutSystems 環境整備

OutSystems セルフトレーニングで、最後に肝心のデザイン変更のところを飛ばしてしまいましたが、そこでは、SILK UI フレームワークのDublin テンプレートを使用することになっていたので、まずは、そちらをインストールします。  
Forge page で「Dublin Template」を検索して、インストールします。<figure class="wp-block-image">

<img src="https://i0.wp.com/www.programmers-office.ml/wp-content/uploads/2019/07/スクリーンショット-2019-07-15-17.28.40.png?ssl=1" alt="" class="wp-image-3111" srcset="https://i0.wp.com/www.programmers-office.ml/wp-content/uploads/2019/07/スクリーンショット-2019-07-15-17.28.40.png?w=800&ssl=1 800w, https://i0.wp.com/www.programmers-office.ml/wp-content/uploads/2019/07/スクリーンショット-2019-07-15-17.28.40.png?resize=300%2C206&ssl=1 300w, https://i0.wp.com/www.programmers-office.ml/wp-content/uploads/2019/07/スクリーンショット-2019-07-15-17.28.40.png?resize=768%2C528&ssl=1 768w" sizes="(max-width: 800px) 100vw, 800px" data-recalc-dims="1" /> </figure> 

そして、アプリケーションの作成。

## Dublinテンプレートによるアプリ作成（失敗）

順に進めていくと、初期画面が出来上がります。<figure class="wp-block-image">

<img src="https://i1.wp.com/www.programmers-office.ml/wp-content/uploads/2019/07/スクリーンショット-2019-07-15-19.29.25-1.png?ssl=1" alt="" class="wp-image-3113" data-recalc-dims="1" /> </figure> <figure class="wp-block-image"><img src="https://i2.wp.com/www.programmers-office.ml/wp-content/uploads/2019/07/スクリーンショット-2019-07-15-19.29.51.png?ssl=1" alt="" class="wp-image-3114" srcset="https://i2.wp.com/www.programmers-office.ml/wp-content/uploads/2019/07/スクリーンショット-2019-07-15-19.29.51.png?w=640&ssl=1 640w, https://i2.wp.com/www.programmers-office.ml/wp-content/uploads/2019/07/スクリーンショット-2019-07-15-19.29.51.png?resize=300%2C244&ssl=1 300w" sizes="(max-width: 640px) 100vw, 640px" data-recalc-dims="1" /></figure> <figure class="wp-block-image"><img src="https://i1.wp.com/www.programmers-office.ml/wp-content/uploads/2019/07/スクリーンショット-2019-07-15-19.30.05.png?ssl=1" alt="" class="wp-image-3115" srcset="https://i1.wp.com/www.programmers-office.ml/wp-content/uploads/2019/07/スクリーンショット-2019-07-15-19.30.05.png?w=640&ssl=1 640w, https://i1.wp.com/www.programmers-office.ml/wp-content/uploads/2019/07/スクリーンショット-2019-07-15-19.30.05.png?resize=300%2C245&ssl=1 300w" sizes="(max-width: 640px) 100vw, 640px" data-recalc-dims="1" /></figure> <figure class="wp-block-image"><img src="https://i1.wp.com/www.programmers-office.ml/wp-content/uploads/2019/07/スクリーンショット-2019-07-15-19.30.47.png?ssl=1" alt="" class="wp-image-3116" srcset="https://i1.wp.com/www.programmers-office.ml/wp-content/uploads/2019/07/スクリーンショット-2019-07-15-19.30.47.png?w=640&ssl=1 640w, https://i1.wp.com/www.programmers-office.ml/wp-content/uploads/2019/07/スクリーンショット-2019-07-15-19.30.47.png?resize=300%2C244&ssl=1 300w" sizes="(max-width: 640px) 100vw, 640px" data-recalc-dims="1" /></figure> <figure class="wp-block-image"><img src="https://i1.wp.com/www.programmers-office.ml/wp-content/uploads/2019/07/スクリーンショット-2019-07-15-19.32.01.png?ssl=1" alt="" class="wp-image-3117" srcset="https://i1.wp.com/www.programmers-office.ml/wp-content/uploads/2019/07/スクリーンショット-2019-07-15-19.32.01.png?w=800&ssl=1 800w, https://i1.wp.com/www.programmers-office.ml/wp-content/uploads/2019/07/スクリーンショット-2019-07-15-19.32.01.png?resize=300%2C138&ssl=1 300w, https://i1.wp.com/www.programmers-office.ml/wp-content/uploads/2019/07/スクリーンショット-2019-07-15-19.32.01.png?resize=768%2C354&ssl=1 768w" sizes="(max-width: 800px) 100vw, 800px" data-recalc-dims="1" /></figure> <figure class="wp-block-image"><img src="https://i0.wp.com/www.programmers-office.ml/wp-content/uploads/2019/07/スクリーンショット-2019-07-15-19.34.03.png?ssl=1" alt="" class="wp-image-3118" srcset="https://i0.wp.com/www.programmers-office.ml/wp-content/uploads/2019/07/スクリーンショット-2019-07-15-19.34.03.png?w=800&ssl=1 800w, https://i0.wp.com/www.programmers-office.ml/wp-content/uploads/2019/07/スクリーンショット-2019-07-15-19.34.03.png?resize=300%2C245&ssl=1 300w, https://i0.wp.com/www.programmers-office.ml/wp-content/uploads/2019/07/スクリーンショット-2019-07-15-19.34.03.png?resize=768%2C627&ssl=1 768w" sizes="(max-width: 800px) 100vw, 800px" data-recalc-dims="1" /></figure> 

一度ここで起動してみるとこんな感じ。<figure class="wp-block-image">

<img src="https://i1.wp.com/www.programmers-office.ml/wp-content/uploads/2019/07/スクリーンショット-2019-07-15-19.35.20.png?ssl=1" alt="" class="wp-image-3119" data-recalc-dims="1" /> </figure> <figure class="wp-block-image"><img src="https://i0.wp.com/www.programmers-office.ml/wp-content/uploads/2019/07/スクリーンショット-2019-07-15-19.36.02.png?ssl=1" alt="" class="wp-image-3120" srcset="https://i0.wp.com/www.programmers-office.ml/wp-content/uploads/2019/07/スクリーンショット-2019-07-15-19.36.02.png?w=640&ssl=1 640w, https://i0.wp.com/www.programmers-office.ml/wp-content/uploads/2019/07/スクリーンショット-2019-07-15-19.36.02.png?resize=300%2C209&ssl=1 300w" sizes="(max-width: 640px) 100vw, 640px" data-recalc-dims="1" /></figure> <figure class="wp-block-image"><img src="https://i1.wp.com/www.programmers-office.ml/wp-content/uploads/2019/07/スクリーンショット-2019-07-15-19.36.29.png?ssl=1" alt="" class="wp-image-3121" srcset="https://i1.wp.com/www.programmers-office.ml/wp-content/uploads/2019/07/スクリーンショット-2019-07-15-19.36.29.png?w=640&ssl=1 640w, https://i1.wp.com/www.programmers-office.ml/wp-content/uploads/2019/07/スクリーンショット-2019-07-15-19.36.29.png?resize=300%2C210&ssl=1 300w" sizes="(max-width: 640px) 100vw, 640px" data-recalc-dims="1" /></figure> 

この辺が、どうも何をしているのか、何をすべきなのかよくわからない。

そして、結局起動できず。<figure class="wp-block-image">

<img src="https://i1.wp.com/www.programmers-office.ml/wp-content/uploads/2019/07/スクリーンショット-2019-07-15-19.58.42.png?ssl=1" alt="" class="wp-image-3123" srcset="https://i1.wp.com/www.programmers-office.ml/wp-content/uploads/2019/07/スクリーンショット-2019-07-15-19.58.42.png?w=800&ssl=1 800w, https://i1.wp.com/www.programmers-office.ml/wp-content/uploads/2019/07/スクリーンショット-2019-07-15-19.58.42.png?resize=300%2C245&ssl=1 300w, https://i1.wp.com/www.programmers-office.ml/wp-content/uploads/2019/07/スクリーンショット-2019-07-15-19.58.42.png?resize=768%2C627&ssl=1 768w" sizes="(max-width: 800px) 100vw, 800px" data-recalc-dims="1" /> </figure> <figure class="wp-block-image"><img src="https://i2.wp.com/www.programmers-office.ml/wp-content/uploads/2019/07/スクリーンショット-2019-07-15-19.58.36.png?ssl=1" alt="" class="wp-image-3122" srcset="https://i2.wp.com/www.programmers-office.ml/wp-content/uploads/2019/07/スクリーンショット-2019-07-15-19.58.36.png?w=800&ssl=1 800w, https://i2.wp.com/www.programmers-office.ml/wp-content/uploads/2019/07/スクリーンショット-2019-07-15-19.58.36.png?resize=300%2C245&ssl=1 300w, https://i2.wp.com/www.programmers-office.ml/wp-content/uploads/2019/07/スクリーンショット-2019-07-15-19.58.36.png?resize=768%2C627&ssl=1 768w" sizes="(max-width: 800px) 100vw, 800px" data-recalc-dims="1" /></figure> 

もしかして、Mac版はダメだけど、Windows版なら、と思ったのですが、ダメでした。一応、画面生成まではできましたが、起動しません。一応、こんな画面ができるという感じです。<figure class="wp-block-image">

<img src="https://i2.wp.com/www.programmers-office.ml/wp-content/uploads/2019/07/list.png?fit=1024%2C566&ssl=1" alt="" class="wp-image-3124" srcset="https://i1.wp.com/www.programmers-office.ml/wp-content/uploads/2019/07/list.png?w=1184&ssl=1 1184w, https://i1.wp.com/www.programmers-office.ml/wp-content/uploads/2019/07/list.png?resize=300%2C166&ssl=1 300w, https://i1.wp.com/www.programmers-office.ml/wp-content/uploads/2019/07/list.png?resize=768%2C425&ssl=1 768w, https://i1.wp.com/www.programmers-office.ml/wp-content/uploads/2019/07/list.png?resize=1024%2C566&ssl=1 1024w" sizes="(max-width: 1000px) 100vw, 1000px" /> </figure> 

Dublinの場合は、左上に、デバイス切り替え機能がつきます。

## 基本テンプレによる画面作成

では基本テンプレートならどうかということ、こちらはできました。

テンプレートとしてTop Menu を選択する以外は、上記Dublinの場合と同じです。

デザイン画面を開いて、おもむろにExcelをインポートしますが、Google スプレッドシートからダウンロードしたものはExcelファイルではないと言われて、失敗しました。一度Office 365 で開いて保存し直したら大丈夫でした。

ただ、シート名、1行目の名称でテーブルを作ってくれると思ったら、それは失敗しました。

まずWindows版だと、ちゃんとシート名を認識はしてくれています。<figure class="wp-block-image">

<img src="https://i1.wp.com/www.programmers-office.ml/wp-content/uploads/2019/07/importexcel.png?ssl=1" alt="" class="wp-image-3125" data-recalc-dims="1" /> </figure> 

これが、Mac版だとこの時点でダメ。<figure class="wp-block-image">

<img src="https://i0.wp.com/www.programmers-office.ml/wp-content/uploads/2019/07/スクリーンショット-2019-07-17-21.22.49.png?ssl=1" alt="" class="wp-image-3126" data-recalc-dims="1" /> </figure> 

で、Windows版でも、Mac版でも、インポート結果はこの通り。<figure class="wp-block-image">

<img src="https://i2.wp.com/www.programmers-office.ml/wp-content/uploads/2019/07/entities.png?ssl=1" alt="" class="wp-image-3127" srcset="https://i2.wp.com/www.programmers-office.ml/wp-content/uploads/2019/07/entities.png?w=120&ssl=1 120w, https://i2.wp.com/www.programmers-office.ml/wp-content/uploads/2019/07/entities.png?resize=113%2C300&ssl=1 113w" sizes="(max-width: 120px) 100vw, 120px" data-recalc-dims="1" /> </figure> 

単なる連番になってしまいました。これは、シート名、項目名が日本語のためかと思われます。

それでも進めることはできます。  
基本テンプレの場合は、初期状態でMainFlowには何もありません。<figure class="wp-block-image">

<img src="https://i0.wp.com/www.programmers-office.ml/wp-content/uploads/2019/07/スクリーンショット-2019-07-17-21.23.09.png?ssl=1" alt="" class="wp-image-3128" srcset="https://i0.wp.com/www.programmers-office.ml/wp-content/uploads/2019/07/スクリーンショット-2019-07-17-21.23.09.png?w=800&ssl=1 800w, https://i0.wp.com/www.programmers-office.ml/wp-content/uploads/2019/07/スクリーンショット-2019-07-17-21.23.09.png?resize=300%2C245&ssl=1 300w, https://i0.wp.com/www.programmers-office.ml/wp-content/uploads/2019/07/スクリーンショット-2019-07-17-21.23.09.png?resize=768%2C627&ssl=1 768w" sizes="(max-width: 800px) 100vw, 800px" data-recalc-dims="1" /> </figure> 

ここにEntity1 を２回ドロップすることで、リスト画面と詳細画面が生成されます。勝手に結合されている状態です。<figure class="wp-block-image">

<img src="https://i2.wp.com/www.programmers-office.ml/wp-content/uploads/2019/07/スクリーンショット-2019-07-17-21.24.53.png?ssl=1" alt="" class="wp-image-3130" srcset="https://i2.wp.com/www.programmers-office.ml/wp-content/uploads/2019/07/スクリーンショット-2019-07-17-21.24.53.png?w=800&ssl=1 800w, https://i2.wp.com/www.programmers-office.ml/wp-content/uploads/2019/07/スクリーンショット-2019-07-17-21.24.53.png?resize=300%2C245&ssl=1 300w, https://i2.wp.com/www.programmers-office.ml/wp-content/uploads/2019/07/スクリーンショット-2019-07-17-21.24.53.png?resize=768%2C627&ssl=1 768w" sizes="(max-width: 800px) 100vw, 800px" data-recalc-dims="1" /> </figure> 

実行する前には、各画面のAnonymous プロパティをチェックOnにします（ログイン画面を表示させないため）。<figure class="wp-block-image">

<img src="https://i1.wp.com/www.programmers-office.ml/wp-content/uploads/2019/07/スクリーンショット-2019-07-17-21.25.25.png?ssl=1" alt="" class="wp-image-3131" data-recalc-dims="1" /> </figure> 

そして起動するとこのような画面が生成されます。明細部分のページングもされていますし、これをスタートとするのは大いにアリでしょう。<figure class="wp-block-image">

<img src="https://i1.wp.com/www.programmers-office.ml/wp-content/uploads/2019/07/スクリーンショット-2019-07-17-21.26.56.png?ssl=1" alt="" class="wp-image-3132" srcset="https://i1.wp.com/www.programmers-office.ml/wp-content/uploads/2019/07/スクリーンショット-2019-07-17-21.26.56.png?w=800&ssl=1 800w, https://i1.wp.com/www.programmers-office.ml/wp-content/uploads/2019/07/スクリーンショット-2019-07-17-21.26.56.png?resize=300%2C207&ssl=1 300w, https://i1.wp.com/www.programmers-office.ml/wp-content/uploads/2019/07/スクリーンショット-2019-07-17-21.26.56.png?resize=768%2C529&ssl=1 768w" sizes="(max-width: 800px) 100vw, 800px" data-recalc-dims="1" /> </figure> <figure class="wp-block-image"><img src="https://i2.wp.com/www.programmers-office.ml/wp-content/uploads/2019/07/スクリーンショット-2019-07-17-21.27.09.png?ssl=1" alt="" class="wp-image-3133" srcset="https://i2.wp.com/www.programmers-office.ml/wp-content/uploads/2019/07/スクリーンショット-2019-07-17-21.27.09.png?w=800&ssl=1 800w, https://i2.wp.com/www.programmers-office.ml/wp-content/uploads/2019/07/スクリーンショット-2019-07-17-21.27.09.png?resize=300%2C60&ssl=1 300w, https://i2.wp.com/www.programmers-office.ml/wp-content/uploads/2019/07/スクリーンショット-2019-07-17-21.27.09.png?resize=768%2C154&ssl=1 768w" sizes="(max-width: 800px) 100vw, 800px" data-recalc-dims="1" /></figure> <figure class="wp-block-image"><img src="https://i2.wp.com/www.programmers-office.ml/wp-content/uploads/2019/07/スクリーンショット-2019-07-17-21.27.24.png?ssl=1" alt="" class="wp-image-3134" srcset="https://i2.wp.com/www.programmers-office.ml/wp-content/uploads/2019/07/スクリーンショット-2019-07-17-21.27.24.png?w=640&ssl=1 640w, https://i2.wp.com/www.programmers-office.ml/wp-content/uploads/2019/07/スクリーンショット-2019-07-17-21.27.24.png?resize=195%2C300&ssl=1 195w" sizes="(max-width: 640px) 100vw, 640px" data-recalc-dims="1" /></figure> 

Glide と違って、参照画面だけでなく、更新画面も生成されます。これは割と大きな違いかもしれません。

ただ、これを完成品としては公開できないかなという感じがあり、その辺が繰り返しになりますが、Glide App と、OutSystems の違いになるような気がします。