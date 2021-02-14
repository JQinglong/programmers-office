---
title: WCFM Marketplace 地図の表示〜Places API
author: KONNO Kiyotaka
type: post
date: 2019-02-02T23:44:30+00:00
archives:
    - 2019
url: /wcfm-marketplace-地図の表示〜places-api/
featured_image: /wp-content/uploads/2019/01/スクリーンショット-2019-01-20-22.17.58.jpg
post_views_count:
  - 676
categories:
  - プログラミング
tags:
  - WCFM

---
地図のプラグインMAPPRESS GOOGLE MAPを入れて、API Keyを設定すると、地図自体は表示されるけれども、入力した住所と連動してくれないという状態でした。

で、productsの地図を入力しようとすると、このようなエラーが。

<blockquote class="wp-block-quote">
  <p>
    Google Maps API Key error: please enable the Places API in the Google Developer Console.
  </p>
</blockquote>

すなわち、Google Maps Platformという大きな括りの中で、大きく三つのサービスが提供されています。そして、そのうちの一つが、Places APIです。  
<a rel="noreferrer noopener" target="_blank" href="https://cloud.google.com/maps-platform/products/?hl=ja&authuser=0">https://cloud.google.com/maps-platform/products/?hl=ja</a><figure class="wp-block-image">

<img src="/uploads/2019/02/スクリーンショット-2019-02-02-22.46.23.jpg?ssl=1" alt="" class="wp-image-2781" srcset="/uploads/2019/02/スクリーンショット-2019-02-02-22.46.23.jpg?w=600&ssl=1 600w, /uploads/2019/02/スクリーンショット-2019-02-02-22.46.23.jpg?resize=300%2C192&ssl=1 300w" sizes="(max-width: 600px) 100vw, 600px" data-recalc-dims="1" /> </figure> 

たしかに、3つ目をチェックしなかった気がします。  
改めて、有効にするのはこちらの画面から。<figure class="wp-block-image">

<img src="/uploads/2019/02/スクリーンショット-2019-02-02-22.48.16.jpg?ssl=1" alt="" class="wp-image-2782" srcset="/uploads/2019/02/スクリーンショット-2019-02-02-22.48.16.jpg?w=800&ssl=1 800w, /uploads/2019/02/スクリーンショット-2019-02-02-22.48.16.jpg?resize=300%2C205&ssl=1 300w, /uploads/2019/02/スクリーンショット-2019-02-02-22.48.16.jpg?resize=768%2C524&ssl=1 768w" sizes="(max-width: 800px) 100vw, 800px" data-recalc-dims="1" /> </figure> 

無事連動するようになりました。