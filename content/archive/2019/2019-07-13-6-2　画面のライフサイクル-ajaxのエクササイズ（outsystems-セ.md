---
title: '6.2　画面のライフサイクル: Ajaxのエクササイズ（OutSystems セルフトレーニング）'
author: KONNO Kiyotaka
type: post
date: 2019-07-13T02:12:50+00:00
archives:
    - 2019
url: /6-2　画面のライフサイクル-ajaxのエクササイズ（outsystems-セ/
featured_image: /wp-content/uploads/2019/06/20190616_231627.jpg
post_views_count:
  - 537
categories:
  - プログラミング
tags:
  - OutSystems

---
テキストによるエクササイズの続きです。<figure class="wp-block-embed-wordpress wp-block-embed is-type-wp-embed is-provider-programmers-office">

<div class="wp-block-embed__wrapper">
  <blockquote class="wp-embedded-content" data-secret="6U8qfzA1YE">
    <a href="https://www.programmers-office.ml/5-7%e3%80%80input-validation%e3%81%ae%e3%82%a8%e3%82%af%e3%82%b5%e3%82%b5%e3%82%a4%e3%82%ba%ef%bc%88outsystems-%e3%82%bb%e3%83%ab%e3%83%95%e3%83%88%e3%83%ac%e3%83%bc%e3%83%8b%e3%83%b3%e3%82%b0/">5.7　Input Validationのエクササイズ（OutSystems セルフトレーニング）</a>
  </blockquote>
</div></figure> 

## Part 1: Add a comments sidebar to movie

Container の幅指定の方法は変わっている。  
Styles Editor を指定。<figure class="wp-block-image">

<img src="/uploads/2019/07/スクリーンショット-2019-07-13-9.30.40.png?ssl=1" alt="" class="wp-image-3073" srcset="/uploads/2019/07/スクリーンショット-2019-07-13-9.30.40.png?w=320&ssl=1 320w, /uploads/2019/07/スクリーンショット-2019-07-13-9.30.40.png?resize=300%2C251&ssl=1 300w" sizes="(max-width: 320px) 100vw, 320px" data-recalc-dims="1" /> </figure> <figure class="wp-block-image"><img src="/uploads/2019/07/スクリーンショット-2019-07-13-9.30.55.png?ssl=1" alt="" class="wp-image-3074" srcset="/uploads/2019/07/スクリーンショット-2019-07-13-9.30.55.png?w=320&ssl=1 320w, /uploads/2019/07/スクリーンショット-2019-07-13-9.30.55.png?resize=259%2C300&ssl=1 259w" sizes="(max-width: 320px) 100vw, 320px" data-recalc-dims="1" /></figure> 

bold 、italic 設定もStyles Editor で。<figure class="wp-block-image">

<img src="/uploads/2019/07/スクリーンショット-2019-07-13-10.34.01.png?ssl=1" alt="" class="wp-image-3075" srcset="/uploads/2019/07/スクリーンショット-2019-07-13-10.34.01.png?w=320&ssl=1 320w, /uploads/2019/07/スクリーンショット-2019-07-13-10.34.01.png?resize=256%2C300&ssl=1 256w" sizes="(max-width: 320px) 100vw, 320px" data-recalc-dims="1" /> </figure> 

CreateUserMovieComment はCoreUserMovieComment の中

<figure class="wp-block-image">

<img src="/uploads/2019/07/スクリーンショット-2019-07-13-11.00.49.png?ssl=1" alt="" class="wp-image-3076" srcset="/uploads/2019/07/スクリーンショット-2019-07-13-11.00.49.png?w=480&ssl=1 480w, /uploads/2019/07/スクリーンショット-2019-07-13-11.00.49.png?resize=150%2C150&ssl=1 150w, /uploads/2019/07/スクリーンショット-2019-07-13-11.00.49.png?resize=300%2C298&ssl=1 300w, /uploads/2019/07/スクリーンショット-2019-07-13-11.00.49.png?resize=64%2C64&ssl=1 64w" sizes="(max-width: 480px) 100vw, 480px" data-recalc-dims="1" /> </figure> 

Assign してReflesh すると言う流れを理解する