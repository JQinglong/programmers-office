---
title: WCFM Marketplace ショップページ
author: KONNO Kiyotaka
type: post
date: 2019-02-03T01:26:35+00:00
archives:
    - 2019
url: /wcfm-marketplace-ショップページ/
featured_image: /wp-content/uploads/2019/01/スクリーンショット-2019-01-20-22.17.58.jpg
post_views_count:
  - 649
categories:
  - プログラミング
tags:
  - WCFM

---
WCFM Marketplaceの設定。各ショップページの設定。  
基本的には、Marketplace→Vndorsで設定していきます。  
デモサイトのこちらの見た目を参考にします。  
<a rel="noreferrer noopener" target="_blank" href="http://wcfmmp.wcfmdemos.com/store/wcfm-vendor/">http://wcfmmp.wcfmdemos.com/store/wcfm-vendor/</a>

気になる点は二つ。  
一つは、STORE HOURS。  
_WCFM MARKETPLACE – STORE HOURS_  
<a rel="noreferrer noopener" target="_blank" href="https://wclovers.com/knowledgebase/wcfm-marketplace-store-hours/">https://wclovers.com/knowledgebase/wcfm-marketplace-store-hours/</a>  
これを見ると、2ヶ所の設定だけで良さそう。念のためと思って、ベンダーユーザでログインしてこのヘルプページと同じ画面でも確認してみましたが、設定はされているけど、公開ショップページには表示されない。  
この辺は、おそらく使用しているテーマにも関係してくる。  
Shop Isleを使っている訳ですが、テーマのカスタマイズで、「Vendor Store Sidebar」という設定項目があり、そこで、Store Hoursを追加できます。<figure class="wp-block-image">

<img src="https://i1.wp.com/www.programmers-office.ml/wp-content/uploads/2019/02/スクリーンショット-2019-02-03-9.53.58.jpg?ssl=1" alt="" class="wp-image-2805" data-recalc-dims="1" /> </figure> 

で、これをやると表示されるようになった訳ですが、ただ、元々表示されていた、商品カテゴリー表示とか、店舗地図とかが消えちゃった。  
まあ、あまりデフォルト表示に頼るのもどうかというのもあるので、必要な表示をここに追加していくことで、だいぶ見た目も整ってきました。  
※用意されているウィジェットも豊富です。<figure class="wp-block-image">

<img src="https://i1.wp.com/www.programmers-office.ml/wp-content/uploads/2019/02/スクリーンショット-2019-02-03-10.03.18.jpg?ssl=1" alt="" class="wp-image-2806" srcset="https://i1.wp.com/www.programmers-office.ml/wp-content/uploads/2019/02/スクリーンショット-2019-02-03-10.03.18.jpg?w=400&ssl=1 400w, https://i1.wp.com/www.programmers-office.ml/wp-content/uploads/2019/02/スクリーンショット-2019-02-03-10.03.18.jpg?resize=199%2C300&ssl=1 199w" sizes="(max-width: 400px) 100vw, 400px" data-recalc-dims="1" /> </figure> 

もう一点は、ABOUTとPOLICIESの入力場所。  
これは、どうやら管理者ログインだと表示されないようで、ベンダーログインして設定。

管理者は全部できるようにしておいて欲しい気もしますが、まあ、良いかと思います。