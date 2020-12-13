---
title: Firebase Hostingにデプロイ
author: KONNO Kiyotaka
type: post
date: 2019-05-29T13:37:55+00:00
url: /firebase-hostingにデプロイ/
featured_image: /wp-content/uploads/2019/05/vuetify.png
post_views_count:
  - 595
categories:
  - プログラミング
tags:
  - Firebase
  - Nuxt.js

---
 

こちらの続き。<figure class="wp-block-embed-wordpress wp-block-embed is-type-wp-embed is-provider-programmers-office">

<div class="wp-block-embed__wrapper">
  <blockquote class="wp-embedded-content" data-secret="k6s5AvBq6M">
    <a href="https://www.programmers-office.ml/vuetify-%e3%81%ae%e5%9f%ba%e6%9c%ac/">Vuetify の基本</a>
  </blockquote>
</div></figure> 

デザインについて、今参考にしているのはVuetify公式サイトのレイアウトサンプル。  
<a href=" https://vuetifyjs.com/ja/framework/pre-made-layouts" target="_blank" rel="noreferrer noopener" aria-label=" (opens in a new tab)">https://vuetifyjs.com/ja/framework/pre-made-layouts</a>

これとかすごいと思いますが、初心者はまだ手を出さないことにします。  
Vue Material Admin  
<a rel="noreferrer noopener" aria-label="https://vuejsprojects.com/vue-material-admin (opens in a new tab)" href="https://vuejsprojects.com/vue-material-admin" target="_blank">https://vuejsprojects.com/vue-material-admin</a>

## Firebase Hostingにデプロイ

引き続き、こちらを参考に。  
Nuxt × TypeScript でTodoListとユーザ認証を実装してFirebase Hostingにデプロイ [Tutorial &#8211; Part 4/5 &#8211; Firebase Hostingにデプロイ]

<https://note.mu/tkugimot/n/n44c327a22c24>

最終的にはGCPにリリースする予定ですが、Firebaseも勉強してみたいので、流れに沿ってやってみます。

<pre class="wp-block-code"><code>npm install -g firebase-tools</code></pre>

でfirebase-toolsのインストール、

<pre class="wp-block-code"><code>firebase login</code></pre>

でログインして、プロジェクト作成して、というところは書いているまま。  
この次の

<pre class="wp-block-code"><code>firebase init</code></pre>

をどこで実行すべきか？  
今現在nuxtアプリを作っている、すなわち、componentsとかlayoutsとかが存在するフォルダで実行します。  
最初  
? What do you want to use as your public directory?  
に対して、初期値のpublicで進めてしまいましたが、distを指定すべき。  
? Configure as a single-page app (rewrite all urls to /index.html)?  
はNoでよいかと。  
ところが、

<pre class="wp-block-code"><code>npm run build</code></pre>

で大量エラー。  
この状態でも

<pre class="wp-block-code"><code> firebase deploy</code></pre>

はできる。この時点では、public内に作成された雛形のindex.htmlが表示される。

よくよく見ると

<pre class="wp-block-code"><code>Module build failed (from ./node_modules/sass-loader/lib/loader.js):
Error: Missing binding・・・
Node Sass could not find a binding for your current environment: OS X 64-bit with Node.js 12.x
Found bindings for the following environments:
  - Linux/musl 64-bit with Node.js 12.x

This usually happens because your environment has changed since running `npm install`.
Run `npm rebuild node-sass` to download the binding for your current environment.
    at module.exports・・・</code></pre>

というようなエラーなので、

<pre class="wp-block-code"><code>npm rebuild node-sass</code></pre>

をやると  
npm run build  
OK！  
npm run generate  
OK！  
しかし、publicではなくdistに作られた  
なので、もう一回firebase init  
上書きを聞いてくれるのでNo

<pre class="wp-block-code"><code>firebase deploy</code></pre>

<a rel="noreferrer noopener" aria-label=" (opens in a new tab)" href="https://titanicfire-d43cd.web.app/" target="_blank">https://titanicfire-d43cd.web.app/</a>

できた！

<div class="kaerebalink-box" style="text-align:left;padding-bottom:20px;font-size:small;zoom: 1;overflow: hidden;">
  <div class="kaerebalink-image" style="float:left;margin:0 15px 10px 0;">
    <a href="//af.moshimo.com/af/c/click?a_id=1238335&#038;p_id=54&#038;pc_id=54&#038;pl_id=616&#038;s_v=b5Rz2P0601xu&#038;url=https%3A%2F%2Fitem.rakuten.co.jp%2Frakutenkobo-ebooks%2F159d6c1b8fe4384aa68d6cfa5d38764d%2F" target="_blank"  rel="noopener noreferrer"><img src="https://i0.wp.com/thumbnail.image.rakuten.co.jp/@0_mall/rakutenkobo-ebooks/cabinet/1742/2000006811742.jpg?ssl=1" style="border: none;" data-recalc-dims="1" /></a><img src="//i.moshimo.com/af/i/impression?a_id=1238335&#038;p_id=54&#038;pc_id=54&#038;pl_id=616" width="1" height="1" style="border:none;" />
  </div>
  
  <div class="kaerebalink-info" style="line-height:120%;zoom: 1;overflow: hidden;">
    <div class="kaerebalink-name" style="margin-bottom:10px;line-height:120%">
      <a href="//af.moshimo.com/af/c/click?a_id=1238335&#038;p_id=54&#038;pc_id=54&#038;pl_id=616&#038;s_v=b5Rz2P0601xu&#038;url=https%3A%2F%2Fitem.rakuten.co.jp%2Frakutenkobo-ebooks%2F159d6c1b8fe4384aa68d6cfa5d38764d%2F" target="_blank"  rel="noopener noreferrer">改訂新版　Vue.jsとFirebaseで作るミニWebサービス【電子書籍】[ 渡邊 達明 ]</a><img src="//i.moshimo.com/af/i/impression?a_id=1238335&#038;p_id=54&#038;pc_id=54&#038;pl_id=616" width="1" height="1" style="border:none;" />
      <div class="kaerebalink-powered-date" style="font-size:8pt;margin-top:5px;font-family:verdana;line-height:120%">
        posted with <a href="https://kaereba.com" rel="nofollow noopener noreferrer" target="_blank">カエレバ</a>
      </div>
    </div>
    <div class="kaerebalink-detail" style="margin-bottom:5px;">
    </div>
    <div class="kaerebalink-link1" style="margin-top:10px;">
      <div class="shoplinkrakuten" style="display:inline;margin-right:5px">
        <a href="//af.moshimo.com/af/c/click?a_id=1238335&#038;p_id=54&#038;pc_id=54&#038;pl_id=616&#038;s_v=b5Rz2P0601xu&#038;url=https%3A%2F%2Fsearch.rakuten.co.jp%2Fsearch%2Fmall%2Ffirebase%2F-%2Ff.1-p.1-s.1-sf.0-st.A-v.2%3Fx%3D0" target="_blank"  rel="noopener noreferrer">楽天市場</a><img src="//i.moshimo.com/af/i/impression?a_id=1238335&#038;p_id=54&#038;pc_id=54&#038;pl_id=616" width="1" height="1" style="border:none;" />
      </div>
      <div class="shoplinkamazon" style="display:inline;margin-right:5px">
        <a href="//af.moshimo.com/af/c/click?a_id=1238337&#038;p_id=170&#038;pc_id=185&#038;pl_id=4062&#038;s_v=b5Rz2P0601xu&#038;url=https%3A%2F%2Fwww.amazon.co.jp%2Fgp%2Fsearch%3Fkeywords%3Dfirebase%26__mk_ja_JP%3D%25E3%2582%25AB%25E3%2582%25BF%25E3%2582%25AB%25E3%2583%258A" target="_blank"  rel="noopener noreferrer">Amazon</a><img src="//i.moshimo.com/af/i/impression?a_id=1238337&#038;p_id=170&#038;pc_id=185&#038;pl_id=4062" width="1" height="1" style="border:none;" />
      </div>
    </div>
  </div>
  
  <div class="booklink-footer" style="clear: left">
  </div>
</div>