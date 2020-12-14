---
title: WCFM Marketplace サイト構成
author: KONNO Kiyotaka
type: post
date: 2019-01-30T14:56:33+00:00
archives:
    - 2019
url: /wcfm-marketplace-サイト構成/
featured_image: /wp-content/uploads/2019/01/スクリーンショット-2019-01-20-22.17.58.jpg
post_views_count:
  - 636
categories:
  - プログラミング
tags:
  - WCFM
  - WooCommerce

---
 

WCFM Marketplaceならではのサイト構成をどう考えるか。

デモサイトを見ると、まず、HOMEPAGEとしては、色々なショップの商品一覧。  
<a rel="noreferrer noopener" target="_blank" href="http://wcfmmp.wcfmdemos.com/">http://wcfmmp.wcfmdemos.com/</a>  
地図があって、検索条件項目があって、商品写真が並ぶ。  
妥当ですね。

ヘッダのリンクは管理画面のリンクも混在していますが、コンシューマ画面と考えた場合に必要なのは、ショップ一覧というのは先日も書いたところ。  
<a rel="noreferrer noopener" target="_blank" href="https://www.programmers-office.ml/2019/01/26/wcfm-marketplace-%E6%9C%80%E5%88%9D%E3%81%AE%E4%B8%80%E6%AD%A9/">https://www.programmers-office.ml/2019/01/26/wcfm-marketplace-%E6%9C%80%E5%88%9D%E3%81%AE%E4%B8%80%E6%AD%A9/</a>

上記デモサイトでは「STORES」から遷移する画面。  
<a rel="noreferrer noopener" target="_blank" href="http://wcfmmp.wcfmdemos.com/stores/">http://wcfmmp.wcfmdemos.com/stores/</a>  
こちらも、地図があって、左サイドにショップの検索項目と、お勧めショップがあって、メインにショップの写真一覧が並ぶ。妥当。

次に必要なのは、各ショップのページ。  
デモサイトで一例を見る。  
<a rel="noreferrer noopener" target="_blank" href="http://wcfmmp.wcfmdemos.com/store/wcfm-vendor/">http://wcfmmp.wcfmdemos.com/store/wcfm-vendor/</a>  
ヘッダに写真があって、左サイドに商品検索、クーポン、営業時間情報、カテゴリ、その他のショップのお勧め、地図、商品おすすめ。メインに商品を並べて、タブ切り替えで、店舗情報、レビュー等。  
妥当。

そして、商品情報。  
<a rel="noreferrer noopener" target="_blank" href="http://wcfmmp.wcfmdemos.com/product/olive-oil/">http://wcfmmp.wcfmdemos.com/product/olive-oil/</a>

とりあえず、全体的にオーソドックスで良いと思いますので、この構成を一つずつ作っていきたいと思います。