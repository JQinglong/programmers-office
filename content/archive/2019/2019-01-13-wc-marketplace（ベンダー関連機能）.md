---
title: WC Marketplace（ベンダー関連機能）
author: KONNO Kiyotaka
type: post
date: 2019-01-13T09:17:32+00:00
url: /wc-marketplace（ベンダー関連機能）/
featured_image: /wp-content/uploads/2019/01/スクリーンショット-2019-01-13-15.55.13.png
post_views_count:
  - 678
categories:
  - プログラミング
tags:
  - WC Marketplace
  - WooCommerce

---
しかし、WooCommerceも日本語情報は、豊富とは言えませんね・・・  
ほとんどお一人で頑張られている？？  
<a rel="noreferrer noopener" target="_blank" href="https://docs.artws.info/about-this-site/">https://docs.artws.info/about-this-site/</a>

WC Marketplaceと言っても、そもそもWooCommerceが分からなければ始まらないので、上記を参考にさせていただきながら、進めていきます。

なお、現時点で、  
WooCommerce Version 3.5.3  
WC Marketplace Version 3.3.0  
です。

## 基本ドキュメント

インストールは、基本レベルだと特に悩まないとは思いますが、  
<a rel="noreferrer noopener" target="_blank" href="https://wc-marketplace.com/knowledgebase/wcmp-setup-guide/">https://wc-marketplace.com/knowledgebase/wcmp-setup-guide/</a>  
一応こちらを参照しておけば、安心かと思います。  
その他のドキュメントも、ここから辿っていきます。

## ベンダー管理システム

Vendors Management System  
<a rel="noreferrer noopener" target="_blank" href="https://wc-marketplace.com/knowledgebase/vendors-submenu/">https://wc-marketplace.com/knowledgebase/vendors-submenu/</a>  
まず、考え方として、Vendorを登録し、これは、wpサイトログインのユーザにもなります。そして一対一でShopが紐付きます。  
基本的には、管理者がVendorユーザを作って、詳細情報はそのVendorユーザが自分自身の情報を登録し、管理者がその登録内容を承認する、という流れのようで、そのためのステータス管理（Pending、Rejected、Suspended、）がされているという形のようです。  
これを登録すると、  
http://localhost/circlant/user1/  
という形で、そのベンダーのページが作成されるのですが、そこに表示される画像はどこで設定するのかが分からない。追々分かることを期待して進めます。

## ベンダー登録方法

Setting up – Vendor Registration for WCMp  
<a rel="noreferrer noopener" target="_blank" href="https://wc-marketplace.com/knowledgebase/setting-vendor-registration-wcmp/">https://wc-marketplace.com/knowledgebase/setting-vendor-registration-wcmp/</a>  
ベンダーについては、より詳細な登録方法として、さらにドキュメントが提供されています。  
管理者が登録する方法以外に、Registration Formも用意されており、それをするしない、承認を経由するしない、フォームで登録する内容、等が設定可能です。  
例えば、Store DescriptionとCountry　を追加すると、このような登録フォームになります。<figure class="wp-block-image">

<img src="https://i2.wp.com/www.programmers-office.ml/wp-content/uploads/2019/01/スクリーンショット-2019-01-13-17.54.17.png?fit=1024%2C754&ssl=1" alt="" class="wp-image-2607" srcset="https://i2.wp.com/www.programmers-office.ml/wp-content/uploads/2019/01/スクリーンショット-2019-01-13-17.54.17.png?w=1690&ssl=1 1690w, https://i2.wp.com/www.programmers-office.ml/wp-content/uploads/2019/01/スクリーンショット-2019-01-13-17.54.17.png?resize=300%2C221&ssl=1 300w, https://i2.wp.com/www.programmers-office.ml/wp-content/uploads/2019/01/スクリーンショット-2019-01-13-17.54.17.png?resize=768%2C565&ssl=1 768w, https://i2.wp.com/www.programmers-office.ml/wp-content/uploads/2019/01/スクリーンショット-2019-01-13-17.54.17.png?resize=1024%2C754&ssl=1 1024w" sizes="(max-width: 1000px) 100vw, 1000px" /> </figure> 

## ベンダー用機能

Setting Up WCMp – A Vendor Guide  
<a rel="noreferrer noopener" target="_blank" href="https://wc-marketplace.com/knowledgebase/setting-wcmp-vendor-guide/">https://wc-marketplace.com/knowledgebase/setting-wcmp-vendor-guide/</a>  
どうもドキュメントの並びが綺麗ではないように思うのですが、ベンダー登録したところで、今度は、ベンダー用機能を見てみます。  
Vendorロールのユーザでwp管理画面にログインすると、ダッシュボードの見た目はだいぶ違います。  
上に書いた、店舗画面の見た目等はここから設定することになります。  
その他、商品や、支払い方法等を登録し、あるいは、注文情報の確認等を行いますが、ポイントは商品登録だと思いますので、今回はここで一旦終了します。