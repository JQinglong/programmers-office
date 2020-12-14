---
title: WC Marketplace（商品機能）
author: KONNO Kiyotaka
type: post
date: 2019-01-13T15:53:13+00:00
archives:
    - 2019
url: /wc-marketplace（商品機能）/
featured_image: /wp-content/uploads/2019/01/スクリーンショット-2019-01-13-15.55.13.png
post_views_count:
  - 659
categories:
  - プログラミング
tags:
  - WC Marketplace
  - WooCommerce

---
商品登録方法は、素のWooCommerceとWC Marketplaceでは考え方が違う部分がありますので、その確認。

## 商品とベンダーの関係

Setting up – Assign Single Product to Multiple Vendors  
<a rel="noreferrer noopener" target="_blank" href="https://wc-marketplace.com/knowledgebase/setting-assign-single-product-multiple-seller/">https://wc-marketplace.com/knowledgebase/setting-assign-single-product-multiple-seller/</a>  
WC Marketplaceプラグインインストール時に、「Single Product Multiple Vendors」というチェックボックスがあります。  
同一商品を複数ベンダーから販売することができ、購入時に顧客がベンダーを選択することができる、というものです。  
これはしないので、スキップします。

## 管理者による商品の登録

Setting up – Uploading products for WCMp  
<a rel="noreferrer noopener" target="_blank" href="https://wc-marketplace.com/knowledgebase/setting-up-uploading-products-for-wcmp/">https://wc-marketplace.com/knowledgebase/setting-up-uploading-products-for-wcmp/</a>  
アップロードから始まるというのが、順番としてどうなのかと思わざるを得ませんが、必須機能ではある、というかむしろ最終的にはこちらが優先なので、これで良いのか。  
・・・と思って読み進めると、別にファイルアップロードの話ではなく、普通に商品登録の話でした。そういう言葉使いですか・・・

最初に、承認を経由するかしないかの設定の話。

そして、管理者が通常のWooCommerceの方法で、商品登録する場合の話。  
ここで、WC Marketplaceが入っていると、ベンダーを指定するプルダウンがあります。これをクリックすると、中身が空で、「？」と悩むのですが、テキストボックスに一文字入力するとそれにマッチするベンダーが選択できるようになります。まあ、ベンダーが大量に登録されていると、ずらっと出てこられても困るかもしれませんが・・・

通常のWooCommerceの商品登録の方法については、  
<a rel="noreferrer noopener" target="_blank" href="https://docs.artws.info/document/managing-products/">https://docs.artws.info/document/managing-products/</a>  
のお世話になるのが良いかと思います。  
特に商品タイプ、特に「バリエーションのある商品」（Variable product）は重要です。

## ベンダーによる商品登録

実際は、商品の登録は各ベンダーがやるでしょう、ということで、その機能についての説明です。  
ベンダーのユーザでログインして、Vendor Dashboard画面に入ります。  
こちらの画面からの登録も、細かい手順や画面構成が異なるのみで、登録内容は基本的に同じです。  
ところが、Product Typeで、「Simple product」しか選択できません。  
他のタイプを選択したい場合は、backendに行かなければならないということです。  
すなわち、ベンダー用画面には、2種類あります。ログイン直後のVendor Dashboard画面と、wp-adminの画面であるbackendです。  
こんなところから移動できます。<figure class="wp-block-image">

<img src="https://i1.wp.com/www.programmers-office.ml/wp-content/uploads/2019/01/スクリーンショット-2019-01-13-23.50.34.png?fit=1024%2C382&ssl=1" alt="" class="wp-image-2612" srcset="https://i0.wp.com/www.programmers-office.ml/wp-content/uploads/2019/01/スクリーンショット-2019-01-13-23.50.34.png?w=1398&ssl=1 1398w, https://i0.wp.com/www.programmers-office.ml/wp-content/uploads/2019/01/スクリーンショット-2019-01-13-23.50.34.png?resize=300%2C112&ssl=1 300w, https://i0.wp.com/www.programmers-office.ml/wp-content/uploads/2019/01/スクリーンショット-2019-01-13-23.50.34.png?resize=768%2C287&ssl=1 768w, https://i0.wp.com/www.programmers-office.ml/wp-content/uploads/2019/01/スクリーンショット-2019-01-13-23.50.34.png?resize=1024%2C382&ssl=1 1024w" sizes="(max-width: 1000px) 100vw, 1000px" /> </figure> 

こちらに移動すれば、機能制限された管理画面が表示される、というわけです。<figure class="wp-block-image">

<img src="https://i1.wp.com/www.programmers-office.ml/wp-content/uploads/2019/01/スクリーンショット-2019-01-13-23.51.53.png?fit=1024%2C670&ssl=1" alt="" class="wp-image-2614" srcset="https://i1.wp.com/www.programmers-office.ml/wp-content/uploads/2019/01/スクリーンショット-2019-01-13-23.51.53.png?w=1850&ssl=1 1850w, https://i1.wp.com/www.programmers-office.ml/wp-content/uploads/2019/01/スクリーンショット-2019-01-13-23.51.53.png?resize=300%2C196&ssl=1 300w, https://i1.wp.com/www.programmers-office.ml/wp-content/uploads/2019/01/スクリーンショット-2019-01-13-23.51.53.png?resize=768%2C502&ssl=1 768w, https://i1.wp.com/www.programmers-office.ml/wp-content/uploads/2019/01/スクリーンショット-2019-01-13-23.51.53.png?resize=1024%2C670&ssl=1 1024w" sizes="(max-width: 1000px) 100vw, 1000px" /> </figure> 

## Advanced Frontend Manager

<a rel="noreferrer noopener" target="_blank" href="https://wc-marketplace.com/knowledgebase/wcmp-frontend-manager/">https://wc-marketplace.com/knowledgebase/wcmp-frontend-manager/</a>  
で、一応、AFMというものを使ってほしそうです。  
これを使えば、backendに移動せずに、「Simple product」以外の商品メンテもできるということです。  
ただ、そんなに、画面からメンテするのか、と考えたら、コスパはあまり良くないかなという気もします。  
<a rel="noreferrer noopener" target="_blank" href="https://wc-marketplace.com/product/wcmp-frontend-manager/">https://wc-marketplace.com/product/wcmp-frontend-manager/</a><figure class="wp-block-image">

<img src="https://i1.wp.com/www.programmers-office.ml/wp-content/uploads/2019/01/スクリーンショット-2019-01-13-23.56.51.png?fit=1024%2C506&ssl=1" alt="" class="wp-image-2613" srcset="https://i2.wp.com/www.programmers-office.ml/wp-content/uploads/2019/01/スクリーンショット-2019-01-13-23.56.51.png?w=2250&ssl=1 2250w, https://i2.wp.com/www.programmers-office.ml/wp-content/uploads/2019/01/スクリーンショット-2019-01-13-23.56.51.png?resize=300%2C148&ssl=1 300w, https://i2.wp.com/www.programmers-office.ml/wp-content/uploads/2019/01/スクリーンショット-2019-01-13-23.56.51.png?resize=768%2C380&ssl=1 768w, https://i2.wp.com/www.programmers-office.ml/wp-content/uploads/2019/01/スクリーンショット-2019-01-13-23.56.51.png?resize=1024%2C506&ssl=1 1024w, https://i2.wp.com/www.programmers-office.ml/wp-content/uploads/2019/01/スクリーンショット-2019-01-13-23.56.51.png?w=2000&ssl=1 2000w" sizes="(max-width: 1000px) 100vw, 1000px" /> </figure> 

という感じで、だいぶ理解はできてきました。