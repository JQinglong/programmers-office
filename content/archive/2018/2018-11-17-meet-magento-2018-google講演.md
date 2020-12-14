---
title: Meet Magento 2018 – Google講演
author: KONNO Kiyotaka
type: post
date: 2018-11-17T07:39:32+00:00
archives:
    - 2018
url: /meet-magento-2018-google講演/
post_views_count:
  - 768
categories:
  - プログラミング
tags:
  - Magento

---
<div class="cl-preview-section">
  <p>
    先日参加した <a href="https://jp.meet-magento.com/meet-magento-2018/" target="_blank" rel="noopener">Meet Magento 2018</a>
  </p>
  
  <p>
    得られたものを書きたいと思いつつ、多すぎてどうしようという状態。
  </p>
</div>

<div class="cl-preview-section">
  <p>
    とりあえず、書きなぐっていきますが、息切れの可能性しかなし。
  </p>
</div>

<div class="cl-preview-section">
  <h2 id="the-path-to-purchase-with-google">
    <a href="https://jp.meet-magento.com/presentation/the-state-of-progressive-web-apps/" target="_blank" rel="noopener">The path to purchase with Google</a>
  </h2>
</div>

<div class="cl-preview-section">
  <p>
    最後はGPayの宣伝！と思いつつ、色々なサービスの紹介が面白かったです。
  </p>
</div>

<div class="cl-preview-section">
  <h3 id="httpshttparchive.org">
    <a href="https://httparchive.org/" target="_blank" rel="noopener">https://httparchive.org/</a>
  </h3>
</div>

<div class="cl-preview-section">
  <p>
    資料を作る際の統計情報的な根拠として、使い勝手がよさそうですね。
  </p>
</div>

<div class="cl-preview-section">
  <h3 id="revenue-impact-calculator">
    revenue impact calculator
  </h3>
</div>

<div class="cl-preview-section">
  <p>
    検索すると、<a href="https://www.thinkwithgoogle.com/feature/mobile/" target="_blank" rel="noopener">https://www.thinkwithgoogle.com/feature/mobile/</a>　に行けと言われるます。で、このサイトを調べようとすると、Domain not found！弱小すぎてダメみたい。
  </p>
</div>

<div class="cl-preview-section">
  <h3 id="lighthouse">
    Lighthouse
  </h3>
</div>

<div class="cl-preview-section">
  <p>
    <a href="https://developers.google.com/web/tools/lighthouse/?hl=ja" target="_blank" rel="noopener">https://developers.google.com/web/tools/lighthouse/?hl=ja</a><br /> に情報がありますが、むしろ簡単なのは、F12デベロッパーツールのAudits。<br /> さらに、セミナーと同日発表になっていますが、<a href="https://developers.google.com/speed/pagespeed/insights/" target="_blank" rel="noopener">PageSpeed Insights</a>　にLighthouseが組み込まれたとのこと。<br /> で、このサイトを調べようとすると、Lighthouse was unable to reliably load the page you requested！<br /> 弱小すぎるにも程がある。
  </p>
</div>

<div class="cl-preview-section">
  <h2 id="lighthouseをもう少し使ってみる">
    Lighthouseをもう少し使ってみる
  </h2>
</div>

<div class="cl-preview-section">
  <p>
    さて、せっかくなので、F12→Autditsをもう少し使ってみます。<br /> <img class="alignnone" src="https://lh3.googleusercontent.com/rGEsiBJ-BZmoz0rTgUSLTTrS-NDoeKPYlCHjLTA1DS1KpIrNcOEOvI5kzQC3XD1DVqpD998nxt6s" alt="F12で表示されるデベロッパーツールのAudits機能" width="512" height="282" /><br /> まず、Performanceから試してみると、画像が大きいよ、と言われます。最近、ページ上部にスライダー画像を付けましたが、早速悪影響があるということで、画像を調整しました。最近アナウンスされた、Googleの<br /> <a href="https://squoosh.app/" target="_blank" rel="noopener">https://squoosh.app/</a><br /> を使ってみました。既存のアップロード済み画像を一気に調整できたらうれしいです。<br /> SEOについては、meta descriptionがないということだけだったので、さっと付けられるところだけ付けていきます。<br /> しかし、問題は、Best practice。<br /> 一番大きい問題は、httpsじゃないよと。<br /> ちょっと調べてみると、xdmainのこの無料の状態では、証明書は入れられないそうです。
  </p>
</div>

<div class="cl-preview-section">
  <h2 id="引っ越し・・・">
    引っ越し・・・
  </h2>
</div>

<div class="cl-preview-section">
  <p>
    ということで、突然のお知らせ。近々サイトを引っ越そうかと思います。<br /> 引っ越し先は、現在借りているさくらレンタルか、GCPか。<a href="https://www.karelie.net/free-fast-wordpress-site/" target="_blank" rel="noopener">https://www.karelie.net/free-fast-wordpress-site/</a>　面白そう・・・
  </p>
  
  <p>
    &nbsp;
  </p>
</div>