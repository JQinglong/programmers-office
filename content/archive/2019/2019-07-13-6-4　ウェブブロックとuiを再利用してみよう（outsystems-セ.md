---
title: 6.4　ウェブブロックとUIを再利用してみよう（OutSystems セルフトレーニング）
author: KONNO Kiyotaka
type: post
date: 2019-07-13T05:45:17+00:00
archives:
    - 2019
url: /6-4　ウェブブロックとuiを再利用してみよう（outsystems-セ/
featured_image: /wp-content/uploads/2019/06/20190616_231627.jpg
post_views_count:
  - 648
categories:
  - プログラミング
tags:
  - OutSystems

---
テキストによるエクササイズの続きです。<figure class="wp-block-embed-wordpress wp-block-embed is-type-wp-embed is-provider-programmers-office">

<div class="wp-block-embed__wrapper">
  <blockquote class="wp-embedded-content" data-secret="GUl4DexpIl">
    <a href="https://www.programmers-office.ml/6-2%e3%80%80%e7%94%bb%e9%9d%a2%e3%81%ae%e3%83%a9%e3%82%a4%e3%83%95%e3%82%b5%e3%82%a4%e3%82%af%e3%83%ab-ajax%e3%81%ae%e3%82%a8%e3%82%af%e3%82%b5%e3%82%b5%e3%82%a4%e3%82%ba%ef%bc%88outsystems-%e3%82%bb/">6.2　画面のライフサイクル: Ajaxのエクササイズ（OutSystems セルフトレーニング）</a>
  </blockquote>
</div></figure> 

## Part 1: Create a Web Block for star ratings

Placeholder のwidth はempty にはできず、Fullにしておく

## Part 2: Make the stars in the Block clickable

Search Box で「Notify」を検索することとなっているが、検索されない。  
<a rel="noreferrer noopener" target="_blank" href="https://www.outsystems.com/forums/discussion/41219/notify-deprecated-in-service-studio-11-what-can-i-use-to-replace-it/">https://www.outsystems.com/forums/discussion/41219/notify-deprecated-in-service-studio-11-what-can-i-use-to-replace-it/</a>  
Manage Dependencies (ctrl + q) で探してくれは良いけど、Deprecated（廃止予定）ってどういうこと？そちらを教えて欲しい・・・

・・・一応その回答はこちら。  
<a rel="noreferrer noopener" target="_blank" href="https://success.outsystems.com/Documentation/11/Developing_an_Application/Design_UI/Reuse_UI/Use_Events_to_Propagate_Changes_From_a_Block_to_the_Parent">https://success.outsystems.com/Documentation/11/Developing_an_Application/Design_UI/Reuse_UI/Use_Events_to_Propagate_Changes_From_a_Block_to_the_Parent</a>  
これまでは、ウェブブロックの中でScreenAction（テキストではStarClicked）を定義して、それをNotifyするという仕組みだったのが、11では、ScreenActionとは別のEventというものが定義できるようになった。  
Notifyのメッセージとして、値等（StarIterator.List.CurrentRowNumber + 1）を定義し、さらに親画面におけるウェブブロックインスタンスのDestinationとしてアクション（OnRatingNotify）を作成して指定する、と言う流れだったのが、バージョン11では、親画面でイベントに対応するハンドラを書く、と言う感じ？<figure class="wp-block-image">

<img src="https://i0.wp.com/www.programmers-office.ml/wp-content/uploads/2019/07/スクリーンショット-2019-07-13-13.58.49.png?ssl=1" alt="" class="wp-image-3081" srcset="https://i0.wp.com/www.programmers-office.ml/wp-content/uploads/2019/07/スクリーンショット-2019-07-13-13.58.49.png?w=320&ssl=1 320w, https://i0.wp.com/www.programmers-office.ml/wp-content/uploads/2019/07/スクリーンショット-2019-07-13-13.58.49.png?resize=159%2C300&ssl=1 159w" sizes="(max-width: 320px) 100vw, 320px" data-recalc-dims="1" /> </figure> <figure class="wp-block-image"><img src="https://i0.wp.com/www.programmers-office.ml/wp-content/uploads/2019/07/スクリーンショット-2019-07-13-13.59.30.png?ssl=1" alt="" class="wp-image-3082" srcset="https://i0.wp.com/www.programmers-office.ml/wp-content/uploads/2019/07/スクリーンショット-2019-07-13-13.59.30.png?w=320&ssl=1 320w, https://i0.wp.com/www.programmers-office.ml/wp-content/uploads/2019/07/スクリーンショット-2019-07-13-13.59.30.png?resize=295%2C300&ssl=1 295w, https://i0.wp.com/www.programmers-office.ml/wp-content/uploads/2019/07/スクリーンショット-2019-07-13-13.59.30.png?resize=64%2C64&ssl=1 64w" sizes="(max-width: 320px) 100vw, 320px" data-recalc-dims="1" /></figure> 

そして、Destinationのアクション（OnRatingNotify）の記述として、Figure 26のような割と複雑なロジックを作っていくわけですが、これはどう書くのだろう・・・

ちょっとテキストがバージョン11に追いついていないので、ここは飛ばしていきます。  
Eventsという形にしたのは悪くないと思うのですが。