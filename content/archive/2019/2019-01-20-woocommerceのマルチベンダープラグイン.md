---
title: WooCommerceのマルチベンダープラグイン
author: KONNO Kiyotaka
type: post
date: 2019-01-20T13:18:55+00:00
archives:
    - 2019
url: /woocommerceのマルチベンダープラグイン/
featured_image: /wp-content/uploads/2019/01/スクリーンショット-2019-01-20-22.17.58.jpg
post_views_count:
  - 1066
categories:
  - プログラミング
tags:
  - WCFM
  - WooCommerce

---
ということで、改めて、WooCommerceのテスト環境を構築しましたが、マルチベンダー構成にするためのプラグインについては、もう少し検討したいと思います。

プラグイン画面で、「multi vendor」で検索すると、いくつかヒットします。この上位4件は割とインストール数も多いですし、更新頻度も高そうです。<figure class="wp-block-image">

<img src="https://i0.wp.com/www.programmers-office.ml/wp-content/uploads/2019/01/スクリーンショット-2019-01-20-21.23.53.jpg?ssl=1" alt="" class="wp-image-2720" srcset="https://i0.wp.com/www.programmers-office.ml/wp-content/uploads/2019/01/スクリーンショット-2019-01-20-21.23.53.jpg?w=800&ssl=1 800w, https://i0.wp.com/www.programmers-office.ml/wp-content/uploads/2019/01/スクリーンショット-2019-01-20-21.23.53.jpg?resize=300%2C161&ssl=1 300w, https://i0.wp.com/www.programmers-office.ml/wp-content/uploads/2019/01/スクリーンショット-2019-01-20-21.23.53.jpg?resize=768%2C412&ssl=1 768w" sizes="(max-width: 800px) 100vw, 800px" data-recalc-dims="1" /> </figure> 

いずれも、日本語対応は弱いので、優劣付けづらいのですが、概ね下記のような感じかと思います。

## WC Marketplace<figure class="wp-block-image">

<img src="https://i0.wp.com/www.programmers-office.ml/wp-content/uploads/2019/01/スクリーンショット-2019-01-20-22.01.53.jpg?fit=1024%2C636&ssl=1" alt="" class="wp-image-2718" srcset="https://i1.wp.com/www.programmers-office.ml/wp-content/uploads/2019/01/スクリーンショット-2019-01-20-22.01.53.jpg?w=2392&ssl=1 2392w, https://i1.wp.com/www.programmers-office.ml/wp-content/uploads/2019/01/スクリーンショット-2019-01-20-22.01.53.jpg?resize=300%2C186&ssl=1 300w, https://i1.wp.com/www.programmers-office.ml/wp-content/uploads/2019/01/スクリーンショット-2019-01-20-22.01.53.jpg?resize=768%2C477&ssl=1 768w, https://i1.wp.com/www.programmers-office.ml/wp-content/uploads/2019/01/スクリーンショット-2019-01-20-22.01.53.jpg?resize=1024%2C636&ssl=1 1024w, https://i1.wp.com/www.programmers-office.ml/wp-content/uploads/2019/01/スクリーンショット-2019-01-20-22.01.53.jpg?w=2000&ssl=1 2000w" sizes="(max-width: 1000px) 100vw, 1000px" /> </figure> 

製品サイト  
<a rel="noreferrer noopener" target="_blank" href="https://wc-marketplace.com/">https://wc-marketplace.com/</a>  
デモサイト  
<a rel="noreferrer noopener" target="_blank" href="http://wcmpdemos.com/WCMp/">http://wcmpdemos.com/WCMp/</a>  
アドオン  
<a rel="noreferrer noopener" target="_blank" href="https://wc-marketplace.com/addons/">https://wc-marketplace.com/addons/</a>  
ドキュメント  
<a rel="noreferrer noopener" target="_blank" href="https://wc-marketplace.com/knowledgebase/">https://wc-marketplace.com/knowledgebase/</a>

・プラグイン自体は無償で、アドオンは有償（割と高め）が多い  
・WooCommerce自体にはstripeの追加プラグインがあるのに、これ用には別途有償アドオンが必要？  
・見た目はそれほど良くはないかな。テーマが豊富に公開されているのは良いけど、ほとんど有償？  
<a rel="noreferrer noopener" target="_blank" href="https://wc-marketplace.com/third-party-themes/">https://wc-marketplace.com/third-party-themes/</a>

## WooCommerce Multivendor Marketplace<figure class="wp-block-image">

<img src="https://i0.wp.com/www.programmers-office.ml/wp-content/uploads/2019/01/スクリーンショット-2019-01-20-22.02.51.jpg?fit=1024%2C728&ssl=1" alt="" class="wp-image-2719" srcset="https://i1.wp.com/www.programmers-office.ml/wp-content/uploads/2019/01/スクリーンショット-2019-01-20-22.02.51.jpg?w=1200&ssl=1 1200w, https://i1.wp.com/www.programmers-office.ml/wp-content/uploads/2019/01/スクリーンショット-2019-01-20-22.02.51.jpg?resize=300%2C213&ssl=1 300w, https://i1.wp.com/www.programmers-office.ml/wp-content/uploads/2019/01/スクリーンショット-2019-01-20-22.02.51.jpg?resize=768%2C546&ssl=1 768w, https://i1.wp.com/www.programmers-office.ml/wp-content/uploads/2019/01/スクリーンショット-2019-01-20-22.02.51.jpg?resize=1024%2C728&ssl=1 1024w" sizes="(max-width: 1000px) 100vw, 1000px" /> </figure> 

製品サイト  
<a rel="noreferrer noopener" target="_blank" href="https://wordpress.org/plugins/wc-multivendor-marketplace/">https://wordpress.org/plugins/wc-multivendor-marketplace/</a>  
デモサイト  
<a rel="noreferrer noopener" target="_blank" href="http://wcfmmp.wcfmdemos.com/stores/">http://wcfmmp.wcfmdemos.com/stores/</a>  
アドオン  
<a rel="noreferrer noopener" target="_blank" href="https://wclovers.com/addons/">https://wclovers.com/addons/</a>  
ドキュメント  
<a rel="noreferrer noopener" target="_blank" href="https://wclovers.com/knowledgebase/">https://wclovers.com/knowledgebase/</a>

・アドオンは少ないけど、安価  
　特にデリバリ機能のアドオンが魅力的  
・オープンソース

## WC Vendors Marketplace

製品サイト  
<a rel="noreferrer noopener" target="_blank" href="https://www.wcvendors.com/">https://www.wcvendors.com/</a>  
アドオン  
<a rel="noreferrer noopener" target="_blank" href="https://www.wcvendors.com/extensions/">https://www.wcvendors.com/extensions/</a>

ドキュメント  
・デモが公開されていないのはなんともしがたい  
・製品自体は、Free版とPro版になっていて、かなりお金がかかりそう

## Dokan<figure class="wp-block-image">

<img src="https://i1.wp.com/www.programmers-office.ml/wp-content/uploads/2019/01/スクリーンショット-2019-01-20-22.00.38.jpg?resize=1024%2C836&#038;ssl=1" alt="" class="wp-image-2722" srcset="https://i1.wp.com/www.programmers-office.ml/wp-content/uploads/2019/01/スクリーンショット-2019-01-20-22.00.38.jpg?resize=1024%2C836&ssl=1 1024w, https://i1.wp.com/www.programmers-office.ml/wp-content/uploads/2019/01/スクリーンショット-2019-01-20-22.00.38.jpg?resize=300%2C245&ssl=1 300w, https://i1.wp.com/www.programmers-office.ml/wp-content/uploads/2019/01/スクリーンショット-2019-01-20-22.00.38.jpg?resize=768%2C627&ssl=1 768w, https://i1.wp.com/www.programmers-office.ml/wp-content/uploads/2019/01/スクリーンショット-2019-01-20-22.00.38.jpg?w=1200&ssl=1 1200w" sizes="(max-width: 1000px) 100vw, 1000px" data-recalc-dims="1" /> </figure> <figure class="wp-block-image"><img src="https://i2.wp.com/www.programmers-office.ml/wp-content/uploads/2019/01/スクリーンショット-2019-01-20-22.00.59.jpg?ssl=1" alt="" class="wp-image-2721" srcset="https://i2.wp.com/www.programmers-office.ml/wp-content/uploads/2019/01/スクリーンショット-2019-01-20-22.00.59.jpg?w=800&ssl=1 800w, https://i2.wp.com/www.programmers-office.ml/wp-content/uploads/2019/01/スクリーンショット-2019-01-20-22.00.59.jpg?resize=300%2C260&ssl=1 300w, https://i2.wp.com/www.programmers-office.ml/wp-content/uploads/2019/01/スクリーンショット-2019-01-20-22.00.59.jpg?resize=768%2C664&ssl=1 768w" sizes="(max-width: 800px) 100vw, 800px" data-recalc-dims="1" /></figure> 

製品サイト  
<a rel="noreferrer noopener" target="_blank" href="https://wedevs.com/dokan/">https://wedevs.com/dokan/</a>  
デモサイト  
<a rel="noreferrer noopener" target="_blank" href="https://dokandemo.wedevs.com/?utm_campaign=dokan_demo_users&utm_medium=dokan_demo_link&utm_source=WordPress.org">https://dokandemo.wedevs.com/?utm_campaign=dokan_demo_users&utm_medium=dokan_demo_link&utm_source=WordPress.org</a>  
アドオン  
<a rel="noreferrer noopener" target="_blank" href="https://wedevs.com/dokan/modules/">https://wedevs.com/dokan/modules/</a>  
ドキュメント  
<a rel="noreferrer noopener" target="_blank" href="https://wedevs.com/docs/dokan/">https://wedevs.com/docs/dokan/</a>

・見た目が美しい  
・これもお金はかかりそう  
・Free機能はオープンソース？  
<a rel="noreferrer noopener" target="_blank" href="https://github.com/weDevsOfficial/dokan">https://github.com/weDevsOfficial/dokan</a>

## 結論

Dokanの見た目はかなり魅力的ですが、オープンソースで、追加アドオンも安価そうなWooCommerce Multivendor Marketplaceで進めてみたいと思います。



<div class="kaerebalink-box" style="text-align:left;padding-bottom:20px;font-size:small;zoom: 1;overflow: hidden;">
  <div class="kaerebalink-image" style="float:left;margin:0 15px 10px 0;">
    <a href="//af.moshimo.com/af/c/click?a_id=1238335&#038;p_id=54&#038;pc_id=54&#038;pl_id=616&#038;s_v=b5Rz2P0601xu&#038;url=https%3A%2F%2Fproduct.rakuten.co.jp%2Fproduct%2F-%2F4215d35b77fae8c2f84c51084aedb473%2F" target="_blank" ><img src="https://i2.wp.com/thumbnail.image.rakuten.co.jp/ran/img/2001/0009/784/798/129/501/20010009784798129501_1.jpg?ssl=1" style="border: none;" data-recalc-dims="1" /></a><img src="//i.moshimo.com/af/i/impression?a_id=1238335&#038;p_id=54&#038;pc_id=54&#038;pl_id=616" width="1" height="1" style="border:none;" />
  </div>
  
  <div class="kaerebalink-info" style="line-height:120%;zoom: 1;overflow: hidden;">
    <div class="kaerebalink-name" style="margin-bottom:10px;line-height:120%">
      <a href="//af.moshimo.com/af/c/click?a_id=1238335&#038;p_id=54&#038;pc_id=54&#038;pl_id=616&#038;s_v=b5Rz2P0601xu&#038;url=https%3A%2F%2Fproduct.rakuten.co.jp%2Fproduct%2F-%2F4215d35b77fae8c2f84c51084aedb473%2F" target="_blank" >小さなＥＣサイトのＷｏｒｄＰｒｅｓｓ＋Ｗｅｌｃａｒｔ導入・設定ガイド 自前でもできる！ /翔泳社/南部正光</a><img src="//i.moshimo.com/af/i/impression?a_id=1238335&#038;p_id=54&#038;pc_id=54&#038;pl_id=616" width="1" height="1" style="border:none;" />
      <div class="kaerebalink-powered-date" style="font-size:8pt;margin-top:5px;font-family:verdana;line-height:120%">
        posted with <a href="https://kaereba.com" rel="nofollow" target="_blank">カエレバ</a>
      </div>
    </div>
    <div class="kaerebalink-detail" style="margin-bottom:5px;">
    </div>
    <div class="kaerebalink-link1" style="margin-top:10px;">
      <div class="shoplinkrakuten" style="display:inline;margin-right:5px">
        <a href="//af.moshimo.com/af/c/click?a_id=1238335&#038;p_id=54&#038;pc_id=54&#038;pl_id=616&#038;s_v=b5Rz2P0601xu&#038;url=https%3A%2F%2Fsearch.rakuten.co.jp%2Fsearch%2Fmall%2FEC%25E3%2582%25B5%25E3%2582%25A4%25E3%2583%2588%2F-%2Ff.1-p.1-s.1-sf.0-st.A-v.2%3Fx%3D0" target="_blank" >楽天市場</a><img src="//i.moshimo.com/af/i/impression?a_id=1238335&#038;p_id=54&#038;pc_id=54&#038;pl_id=616" width="1" height="1" style="border:none;" />
      </div>
      <div class="shoplinkamazon" style="display:inline;margin-right:5px">
        <a href="//af.moshimo.com/af/c/click?a_id=1238337&#038;p_id=170&#038;pc_id=185&#038;pl_id=4062&#038;s_v=b5Rz2P0601xu&#038;url=https%3A%2F%2Fwww.amazon.co.jp%2Fgp%2Fsearch%3Fkeywords%3DEC%25E3%2582%25B5%25E3%2582%25A4%25E3%2583%2588%26__mk_ja_JP%3D%25E3%2582%25AB%25E3%2582%25BF%25E3%2582%25AB%25E3%2583%258A" target="_blank" >Amazon</a><img src="//i.moshimo.com/af/i/impression?a_id=1238337&#038;p_id=170&#038;pc_id=185&#038;pl_id=4062" width="1" height="1" style="border:none;" />
      </div>
      <div class="shoplinkseven" style="display:inline;margin-right:5px">
        <a href="//af.moshimo.com/af/c/click?a_id=1238336&#038;p_id=932&#038;pc_id=1188&#038;pl_id=12456&#038;s_v=b5Rz2P0601xu&#038;url=http%3A%2F%2F7net.omni7.jp%2Fsearch%2F%3Fkeyword%3DEC%25E3%2582%25B5%25E3%2582%25A4%25E3%2583%2588%26searchKeywordFlg%3D1" target="_blank" ><img src="//i.moshimo.com/af/i/impression?a_id=1238336&p_id=932&pc_id=1188&pl_id=12456" width="1" height="1" style="border:none;">7net</a>
      </div>
    </div>
  </div>
  
  <div class="booklink-footer" style="clear: left">
  </div>
</div>