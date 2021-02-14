---
title: WooCommerceを試す
author: KONNO Kiyotaka
type: post
date: 2019-01-13T01:52:34+00:00
archives:
    - 2019
url: /woocommerceを試す/
featured_image: /wp-content/uploads/2019/01/スクリーンショット-2019-01-13-0.22.01.png
post_views_count:
  - 561
categories:
  - プログラミング
tags:
  - Docker
  - WooCommerce

---
MagentoのDocker環境を作った訳ですが、サンプルデータを後から投入しようとすると、やはり、「PHP Fatal error: Allowed memory size of xxx bytes exhausted」が発生したりして、Dockerの出来合いの環境ならもう少しすんなり行くかなと言う期待は、あまり応えてはもらえませんでした。

そこで、ちょっと浮気をしてみます。  
Docker力強化も兼ねて、今回もDocker環境を作ります。  
WooCommerce入りのDocker Hubのイメージもありますが、そこは後からプラグイン入れても良いよね、ということでwordpress環境をまず作ります。  
イメージは、あえて公式ではなく、先日の構成を参考にして、bitnami版にしてみます。

今回は、最初から、ymlに永続化用の記述をしておきます。

<blockquote class="wp-block-quote">
  <p>
    mkdir docker/WooCommerce<br />mkdir docker/WooCommerce/wc-mariadb-persistence<br />mkdir docker/WooCommerce/wc-wordpress-persistence<br />cd docker/WooCommerce/<br />curl -LO https://raw.githubusercontent.com/bitnami/bitnami-docker-wordpress/master/docker-compose.yml<br />・・・yml編集・・・<br />docker-compose up -d
  </p>
</blockquote>

  
やはり、wordpressセットアップ画面をすっ飛ばして、サイトが立ち上がっている状態まで来てくれます。<figure class="wp-block-image">

<img src="/uploads/2019/01/スクリーンショット-2019-01-13-0.22.01.png?fit=1024%2C710&ssl=1" alt="" class="wp-image-2601" srcset="/uploads/2019/01/スクリーンショット-2019-01-13-0.22.01.png?w=2286&ssl=1 2286w, /uploads/2019/01/スクリーンショット-2019-01-13-0.22.01.png?resize=300%2C208&ssl=1 300w, /uploads/2019/01/スクリーンショット-2019-01-13-0.22.01.png?resize=768%2C532&ssl=1 768w, /uploads/2019/01/スクリーンショット-2019-01-13-0.22.01.png?resize=1024%2C710&ssl=1 1024w, /uploads/2019/01/スクリーンショット-2019-01-13-0.22.01.png?w=2000&ssl=1 2000w" sizes="(max-width: 1000px) 100vw, 1000px" /> </figure> 

管理画面はwp-admin、ユーザ・パスワードは、Settings画面参照（WORDPRESS\_USERNAME、WORDPRESS\_PASSWORD）。  
日本語化はされていません。

そして、おもむろに、Pluginsから、WooCommerceをInstall、Activate。PluginsのページにWelcome to WooCommerceのメッセージと「Run the Setup Wizard」ボタンが表示されているので、クリックします。  
基本情報を入力し、Payment画面では、PayPalとstripe、さらにCash on deliveryを有効にしてみます。Shippingはとりあえず適当に、オススメのAutomated TaxesとMailChimpも有効にしておいて、Jetpackは接続できないというメッセージになりましたがそのまま行きます。  
チュートリアルに従って商品登録し、「Visit Site」の下の「Visit Shop」をクリックすると、商品が表示され、カートに投入し、カートを見ると購入商品が表示されます。

ただ、この状態ではあまりに見た目が投げやりなので、AppearanceのThemesからStorefront を検索して、Install、Activateします。  
「Design your store」という画面が表示されますので、流れに従って入力。多少見た目が整います。「Design your store」が公式のようなので入れてみましたが、なかなかのシンプルさではあります。  
<a rel="noreferrer noopener" target="_blank" href="https://shimesan.com/2018/03/24/woocommerce-netshop-003/">https://shimesan.com/2018/03/24/woocommerce-netshop-003/</a>  
この辺は参考になりそうです。  
試しにもう一つ、THESHOPというテーマを入れてみます。  
<a rel="noreferrer noopener" target="_blank" href="https://athemes.com/theme/theshop/#">https://athemes.com/theme/theshop/#</a>  
さすがの良い感じ。  
とりあえず、こうしておきます。

さらに、今回やりたいのは単一ショップではないので、複数ベンダー対応のプラグイン、「WC Marketplace」を入れます。  
そして、ちょっと設定を初めてみましたが、これはなかなか骨が折れそうなので、また改めて。