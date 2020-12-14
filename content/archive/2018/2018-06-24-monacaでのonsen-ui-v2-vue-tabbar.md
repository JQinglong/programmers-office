---
title: MonacaでのOnsen UI V2 Vue Tabbar
author: KONNO Kiyotaka
type: post
date: 2018-06-24T06:58:31+00:00
archives:
    - 2018
url: /monacaでのonsen-ui-v2-vue-tabbar/
post_views_count:
  - 1150
categories:
  - プログラミング

---
まず、Monacaで画面デザインを作っています。  
新規プロジェクトでは、「Onsen UI V2 Vue Tabbar」を選択します。

[<img style="display: inline; background-image: none;" title="monaca_newprj" src="https://i2.wp.com/www.programmers-office.ml/wp-content/uploads/2018/06/monaca_newprj_thumb.png?resize=244%2C172&#038;ssl=1" alt="monaca_newprj" width="244" height="172" border="0" data-recalc-dims="1" />][1]  
しかし、各種サンプルを見ながらなんとかなるかなと思いいつつ、なかなかしんどいですね。

この構成の場合、何かを調べようと思ったら、Monacaという基盤の話なのか、Onsen UIというデザインフレームワークの話なのか、Vueという画面制御フレームワークの話なのか、を切り分けながらそれぞれのマニュアルなり、情報なりを調べる必要があるわけです。

で、いきなり、はまったのが、画面上部のツールバーに画像を表示したいな、と。  
そこで考えるべきは、画像をどこに置くのか、どういうパスを書けば参照してくれるのか、普通にimgタグを使うべきなのか、他に作法があるのか、等ですが、それぞれの守備範囲がいまいち理解できずに、調べようがないなと思うわけです。

結論としては、サンプルとして公開されているポケモンアプリ（<a href="https://docs.monaca.io/ja/sampleapp/samples/" target="_blank" rel="noopener">https://docs.monaca.io/ja/sampleapp/samples/</a>）で、画像の置き場はsrc/publicか、と理解し、あとはimgタグでやってみて、うまくいっているからよいか、みたいな感じです。

もう一つの例としては、画面を黒系統にしたいなと思い、Onsen UIのテーマローラー（<a href="https://onsen.io/theme-roller/" target="_blank" rel="noopener">https://onsen.io/theme-roller/</a>）というのでDark themeといのがあるのが分かったのですが、それの適用方法が分からない。見てるとテーマローラーで生成したファイル群をダウンロードして、配置して、という方法が出てきますが、細かくカスタマイズしたいならそうかもしれませんが、単にテーマを適用したいだけなんだよ、ということでもう少し調べると、onsen-css-components.cssをonsen-css-components-dark-theme.cssに書き換えればよい、という情報が見つかります。  
これはどこに書いてあるのだ、というところから始まりますが、それは検索して、今回の構成の場合はmain.jsに書いてあることが分かります。cssの読み込みをjsでやる、というところで既に古い頭にはつらいのですが、そういうものです。  
ところが、このように書き換えてみても反映されない。むむ、と思い、もう少し調べると、dark-onsen-css-components.cssだよ、という情報が見つかり、これでOK。

しかし、なかなか辿り着かないよ、と思いつつ、やっていくうちに馴染むだろうと思い込んで、先に進みます。

<table style="border: currentcolor;" border="0" cellpadding="5">
  <tr>
    <td style="border: currentcolor; text-align: left;">
      <a href="https://www.amazon.co.jp/exec/obidos/ASIN/4774197068/jqinglong-22/" target="_blank" rel="noopener">React、Angular、Vue.js、React Nativeを使って学ぶ はじめてのフロントエンド開発</a>
    </td>
  </tr>
  
  <tr>
    <td style="border: currentcolor;">
      <table style="border: currentcolor;" border="0" cellpadding="0">
        <tr>
          <td style="border: currentcolor;" valign="top">
            <a href="https://www.amazon.co.jp/exec/obidos/ASIN/4774197068/jqinglong-22/" target="_blank" rel="noopener"><img style="margin-right: 10px;" src="https://i2.wp.com/images-fe.ssl-images-amazon.com/images/I/51UKPfcT0yL._SL160_.jpg?ssl=1" border="0" data-recalc-dims="1" /></a>
          </td>
          <td style="border: currentcolor; text-align: left;" valign="top">
            <div class="kaerebalink-detail" style="margin-bottom: 5px;">
              原 一浩,taisa,小松 大輔,永井 孝,池内 孝啓,新井 正貴,橋本 安司,日野 洋一郎 技術評論社 2018-05-09
            </div>
            
            <div class="kaerebalink-salesranking" style="margin-bottom: 5px;">
              売り上げランキング : 8419
            </div>
            
            <table style="border: currentcolor; margin-top: 10px;">
              <tr>
                <td style="border: currentcolor; text-align: left;">
                </td>
                
                <td style="border: currentcolor; padding-left: 10px; font-size: x-small; vertical-align: bottom;">
                  by <a href="https://kaereba.com" target="_blank" rel="nofollow noopener">カエレバ</a>
                </td>
              </tr>
            </table>
          </td>
        </tr>
      </table>
    </td>
  </tr>
</table>

 [1]: https://i2.wp.com/www.programmers-office.ml/wp-content/uploads/2018/06/monaca_newprj.png?ssl=1