---
title: WCFM Marketplace Homepage設定
author: KONNO Kiyotaka
type: post
date: 2019-01-31T16:00:36+00:00
excerpt: |
  今日のメインは地図。
  地図の表示にあたっては、他のプラグインとの連携が考えられているようです。
archives:
    - 2019
url: /wcfm-marketplace-homepage設定/
featured_image: /wp-content/uploads/2019/01/スクリーンショット-2019-01-20-22.17.58.jpg
post_views_count:
  - 798
categories:
  - プログラミング
tags:
  - WCFM
  - WooCommerce

---
## Homepageに表示する固定ページ

設定画面のReadingから「Homepage」にショップページを指定します。<figure class="wp-block-image">

<img src="/uploads/2019/02/スクリーンショット-2019-01-31-7.16.08.jpg?fit=1024%2C753&ssl=1" alt="" class="wp-image-2761" srcset="/uploads/2019/02/スクリーンショット-2019-01-31-7.16.08.jpg?w=1596&ssl=1 1596w, /uploads/2019/02/スクリーンショット-2019-01-31-7.16.08.jpg?resize=300%2C221&ssl=1 300w, /uploads/2019/02/スクリーンショット-2019-01-31-7.16.08.jpg?resize=768%2C565&ssl=1 768w, /uploads/2019/02/スクリーンショット-2019-01-31-7.16.08.jpg?resize=1024%2C753&ssl=1 1024w" sizes="(max-width: 1000px) 100vw, 1000px" /> </figure> 

最初Wordpressインストール時に日本語指定していたからか、日本語になってしまってますが、WooCommerce本体としてのトップページであり、これがWCFM Marketplaceでは、全店舗横断の商品ページ、という位置付けになります。  
「Posts page」は指定すると、その画面はブログページになってしまうので、必要な場合はそれ用の固定ページを作る、ブログが不要な場合は非表示のページを指定しておく、というような形で良いかと思います。

## 地図

今日のメインは地図。  
地図の表示にあたっては、他のプラグインとの連携が考えられているようです。  
_DOCUMENTATION_  
<a rel="noreferrer noopener" target="_blank" href="https://wclovers.com/knowledgebase/">https://wclovers.com/knowledgebase/</a>

この中で、INTEGRATIONSに挙げられている地図関連のものが3つ。  
どれを使っても良いのかなというのは、それぞれの紹介文面から見て取れます。

_WCFM – MAPPRESS GOOGLE MAP_  
<a rel="noreferrer noopener" target="_blank" href="https://wclovers.com/knowledgebase/wcfm-mappress-google-map/">https://wclovers.com/knowledgebase/wcfm-mappress-google-map/</a>

<blockquote class="wp-block-quote">
  <p>
    In recent days Map – Google Map is very much essential to inform about your store/product location to your customers.
  </p>
  
  <p>
    “MapPress Easy Google Map” is one of the most easiest and user friendly plugin to do so. You can associate any number of maps with your product and also allowed any no of points within a single map, isn’t it really cool!!
  </p>
</blockquote>

_WCFM – GEO MY WP_  
<a rel="noreferrer noopener" target="_blank" href="https://wclovers.com/knowledgebase/wcfm-geo-wp/">https://wclovers.com/knowledgebase/wcfm-geo-wp/</a>

<blockquote class="wp-block-quote">
  <p>
    In recent days Map – Google Map is very much essential to inform about your store/product location to your customers.
  </p>
  
  <p>
    “GEO my WP” is one of the most easiest and user friendly plugin to do so. You can associate location info and address with your product , isn’t it really cool!!
  </p>
</blockquote>

_WCFM – TOOLSET MAPS_  
<a rel="noreferrer noopener" target="_blank" href="https://wclovers.com/knowledgebase/wcfm-toolset-maps/">https://wclovers.com/knowledgebase/wcfm-toolset-maps/</a>

<blockquote class="wp-block-quote">
  <p>
    In recent days Map – Google Map is very much essential to inform about your store/product location to your customers.
  </p>
  
  <p>
    “Toolset Maps” is one of the most easiest and user friendly plugin to do so. You can associate location info and address with your product , isn’t it really cool!!
  </p>
</blockquote>

で、並べてみると分かるように、「WCFM – MAPPRESS GOOGLE MAP」だけ、一つの地図に複数のポイントを表示することができる、みたいなことを書いているので、それを使ってみることにします。

## MAPPRESS GOOGLE MAP

これ自体のページはこちら。  
<a rel="noreferrer noopener" target="_blank" href="https://ja.wordpress.org/plugins/mappress-google-maps-for-wordpress/">https://ja.wordpress.org/plugins/mappress-google-maps-for-wordpress/</a>  
検索すれば日本語情報も豊富なので安心です。  
インストールは普通にプラグインの新規追加で検索。  
アクティベートしたらMapPressメニューからMappingEngineにGoogleを指定。そして、API Keyを指定。

ちょっと気になるのは商品への関連付けの説明しかないこと。  
こちらの画面でも、Productsとの関連付けはありますが、Shop(Store, Vendor)はありません。  
確かに、Productsの追加画面には地図機能が追加されます。（要はホテル等向けということですかね）<figure class="wp-block-image">

<img src="/uploads/2019/02/スクリーンショット-2019-02-01-0.09.55.jpg?fit=1024%2C512&ssl=1" alt="" class="wp-image-2763" srcset="/uploads/2019/02/スクリーンショット-2019-02-01-0.09.55.jpg?w=1400&ssl=1 1400w, /uploads/2019/02/スクリーンショット-2019-02-01-0.09.55.jpg?resize=300%2C150&ssl=1 300w, /uploads/2019/02/スクリーンショット-2019-02-01-0.09.55.jpg?resize=768%2C384&ssl=1 768w, /uploads/2019/02/スクリーンショット-2019-02-01-0.09.55.jpg?resize=1024%2C512&ssl=1 1024w" sizes="(max-width: 1000px) 100vw, 1000px" /> </figure> 

しかし、API Keyの指定はもう一箇所あります。  
Marketplaceのメニューから、SettingsのMarketplace SettingsのGoogle Map API KeyGoogle。これを入力すると、自動的にショップページの上部に地図が表示されます。  
そして、この状態でVendors画面を見ると、Store Locationの部分に地図が表示されています。ここでロケーションを設定すれば良いはずですが、住所を入力しても反応してくれない。<figure class="wp-block-image">

<img src="/uploads/2019/02/スクリーンショット-2019-02-01-0.29.38-1.jpg?fit=1024%2C783&ssl=1" alt="" class="wp-image-2764" srcset="/uploads/2019/02/スクリーンショット-2019-02-01-0.29.38-1.jpg?w=1370&ssl=1 1370w, /uploads/2019/02/スクリーンショット-2019-02-01-0.29.38-1.jpg?resize=300%2C229&ssl=1 300w, /uploads/2019/02/スクリーンショット-2019-02-01-0.29.38-1.jpg?resize=768%2C587&ssl=1 768w, /uploads/2019/02/スクリーンショット-2019-02-01-0.29.38-1.jpg?resize=1024%2C783&ssl=1 1024w" sizes="(max-width: 1000px) 100vw, 1000px" /> </figure> 

ここで一旦中断します。