---
title: OutSystemsによるローコード開発？
author: KONNO Kiyotaka
type: post
date: 2019-06-23T12:36:57+00:00
url: /outsystemsによるローコード開発？/
featured_image: /wp-content/uploads/2019/06/outsystems2.png
post_views_count:
  - 665
categories:
  - プログラミング
tags:
  - OutSystems

---
先ほど色々システム構成図の画像をアップした中に、OutSystemsのものがあります。

## OutSystemsとは

日本公式サイトだと、「コードレス開発」を謳っていますが、「ローコード開発」とか、色々言い方はあるようで。ソース生成型のツールで、いざとなったらソースいじることもできるようなので、「ローコード開発」の方がよいのでは。

<a href="http://www.bluememe.jp/outsystems/product/product-devops-dev.html" target="_blank" rel="noreferrer noopener" aria-label=" (opens in a new tab)">http://www.bluememe.jp/outsystems/product/product-devops-dev.html</a>

ASP.NETかJavaのソースを出力してくれるそうです。あまり何も考えずにチュートリアルをやってみたら、ASP.NET＋SQL Serverの環境を作ってくれたようです。<figure class="wp-block-image">

<img src="https://i0.wp.com/www.programmers-office.ml/wp-content/uploads/2019/06/outsystems1.png?ssl=1" alt="" class="wp-image-3003" srcset="https://i0.wp.com/www.programmers-office.ml/wp-content/uploads/2019/06/outsystems1.png?w=878&ssl=1 878w, https://i0.wp.com/www.programmers-office.ml/wp-content/uploads/2019/06/outsystems1.png?resize=300%2C237&ssl=1 300w, https://i0.wp.com/www.programmers-office.ml/wp-content/uploads/2019/06/outsystems1.png?resize=768%2C608&ssl=1 768w" sizes="(max-width: 878px) 100vw, 878px" data-recalc-dims="1" /> </figure> 

## チュートリアルをやってみて

以前、Glide をやってみた時、<figure class="wp-block-embed-wordpress wp-block-embed is-type-wp-embed is-provider-programmers-office">

<div class="wp-block-embed__wrapper">
  <blockquote class="wp-embedded-content" data-secret="6atGfG8RvH">
    <a href="https://www.programmers-office.ml/glide%e3%81%ae%e5%91%b3%e3%82%8f%e3%81%84%e6%96%b9%e3%80%9c%e3%82%aa%e3%83%bc%e3%83%97%e3%83%b3%e3%83%87%e3%83%bc%e3%82%bf%e3%82%92%e6%b4%bb%e7%94%a8%e3%81%97%e3%82%88%e3%81%86/">Glideの味わい方〜オープンデータを活用しよう</a>
  </blockquote>
</div></figure> 

これは、本当に何もしないんだな、まさにコードレスだなと思いましたが、かなり近いところまで行っているようにも思います。

画面テンプレートを選択すると、サンプルデータで動く形までできていて、EXCELデータを指定すると、それをDBに登録して、そちらを参照するように変更してくれる、というのはスマートな作りだと思います。<figure class="wp-block-image">

<img src="https://i0.wp.com/www.programmers-office.ml/wp-content/uploads/2019/06/outsystems2.png?resize=1024%2C478&#038;ssl=1" alt="" class="wp-image-3002" srcset="https://i0.wp.com/www.programmers-office.ml/wp-content/uploads/2019/06/outsystems2.png?resize=1024%2C478&ssl=1 1024w, https://i0.wp.com/www.programmers-office.ml/wp-content/uploads/2019/06/outsystems2.png?resize=300%2C140&ssl=1 300w, https://i0.wp.com/www.programmers-office.ml/wp-content/uploads/2019/06/outsystems2.png?resize=768%2C358&ssl=1 768w, https://i0.wp.com/www.programmers-office.ml/wp-content/uploads/2019/06/outsystems2.png?w=1292&ssl=1 1292w" sizes="(max-width: 1000px) 100vw, 1000px" data-recalc-dims="1" /> </figure> 

このような画面を作るのですが、リスト用のデータと、グラフ用のデータをそれぞれ指定するだけでここまでできてしまいます。リストから詳細ページへの流れも、詳細画面は勝手にそれっぽく作ってくれるという点で、Glideと同様の発想かと思います。

.NETと言っているのでWindows版だけかと思ったら、technical previewとしてはmac版も提供されていました。

<a href="https://success.outsystems.com/Support/Enterprise_Customers/Maintenance_and_Operations/OutSystems_Service_Studio_for_Mac" target="_blank" rel="noreferrer noopener" aria-label=" (opens in a new tab)">https://success.outsystems.com/Support/Enterprise_Customers/Maintenance_and_Operations/OutSystems_Service_Studio_for_Mac</a>

個人用フリー版が用意されているのもうまいと思います。私も、もう少し使ってみたいと感じました。