---
title: XamarinのXAMLのデザイナー
author: KONNO Kiyotaka
type: post
date: 2018-10-13T14:11:23+00:00
archives:
    - 2018
url: /xamarinのxamlのデザイナー/
post_views_count:
  - 794
categories:
  - プログラミング
tags:
  - Xamarin

---
Xamarinも楽ではないですなー

## Xamarinのチュートリアル

<a href="https://docs.microsoft.com/ja-jp/xamarin/xamarin-forms/get-started/hello-xamarin-forms/quickstart?tabs=vswin" target="_blank" rel="noopener noreferrer">https://docs.microsoft.com/ja-jp/xamarin/xamarin-forms/get-started/hello-xamarin-forms/quickstart?tabs=vswin</a>

で、最初のとっかかりは良かったのですが、構成がいまいちまとまりきっておらず、内容もビデオを見たりするのが多いのでちょっと進めにくい。  
ということで、こちらをやってみようと思います。

<div class="kaerebalink-box" style="text-align: left; overflow: hidden; padding-bottom: 20px; font-size: small; -ms-zoom: 1;">
  <div class="kaerebalink-image" style="margin: 0px 15px 10px 0px; float: left;">
    <a href="https://www.amazon.co.jp/exec/obidos/ASIN/B01N7NI08L/konnokiyotaka-22/" target="_blank" rel="noopener noreferrer"><img style="border: currentcolor;" src="https://i0.wp.com/images-fe.ssl-images-amazon.com/images/I/41tB8RffAyL._SL160_.jpg?ssl=1" data-recalc-dims="1" /></a>
  </div>
  
  <div class="kaerebalink-info" style="line-height: 120%; overflow: hidden; -ms-zoom: 1;">
    <div class="kaerebalink-name" style="line-height: 120%; margin-bottom: 10px;">
      <p>
        <a href="https://www.amazon.co.jp/exec/obidos/ASIN/B01N7NI08L/konnokiyotaka-22/" target="_blank" rel="noopener noreferrer">かずきのXamarin.Forms入門</a>
      </p>
      <div class="kaerebalink-powered-date" style="line-height: 120%; font-family: verdana; font-size: 8pt; margin-top: 5px;">
        posted with <a href="https://kaereba.com" target="_blank" rel="nofollow noopener noreferrer">カエレバ</a>
      </div>
    </div>
    <div class="kaerebalink-detail" style="margin-bottom: 5px;">
      大田　一希 2016-12-29
    </div>
    <div class="kaerebalink-link1" style="margin-top: 10px;">
      <div class="shoplinkamazon" style="margin-right: 5px; display: inline;">
        <a href="https://www.amazon.co.jp/gp/search?keywords=xamarin%20%E3%81%8B%E3%81%9A%E3%81%8D&__mk_ja_JP=%E3%82%AB%E3%82%BF%E3%82%AB%E3%83%8A&tag=konnokiyotaka-22" target="_blank" rel="noopener noreferrer">Amazon</a>
      </div>
      <div class="shoplinkrakuten" style="margin-right: 5px; display: inline;">
        <a href="//af.moshimo.com/af/c/click?a_id=762690&p_id=54&pc_id=54&pl_id=616&s_v=b5Rz2P0601xu&url=https%3A%2F%2Fsearch.rakuten.co.jp%2Fsearch%2Fmall%2Fxamarin%2520%25E3%2581%258B%25E3%2581%259A%25E3%2581%258D%2F-%2Ff.1-p.1-s.1-sf.0-st.A-v.2%3Fx%3D0" target="_blank" rel="noopener noreferrer">楽天市場</a><img style="border: currentcolor;" src="//i.moshimo.com/af/i/impression?a_id=762690&p_id=54&pc_id=54&pl_id=616" width="1" height="1" />
      </div>
      <div class="shoplinkseven" style="margin-right: 5px; display: inline;">
        <a href="//af.moshimo.com/af/c/click?a_id=762691&p_id=932&pc_id=1188&pl_id=12456&s_v=b5Rz2P0601xu&url=http%3A%2F%2F7net.omni7.jp%2Fsearch%2F%3Fkeyword%3Dxamarin%2520%25E3%2581%258B%25E3%2581%259A%25E3%2581%258D%26searchKeywordFlg%3D1" target="_blank" rel="noopener noreferrer"><img style="border: currentcolor;" src="//i.moshimo.com/af/i/impression?a_id=762691&p_id=932&pc_id=1188&pl_id=12456" width="1" height="1" />7net</a>
      </div>
    </div>
  </div>
  
  <div class="booklink-footer" style="clear: left;">
  </div>
</div>

（もうすこし画像何とかすればよいのにと思いますが。もったいない・・・）

16ページ  
StackLayout.Children  
省略可能となっているが、そもそも廃止されてないかな？？

## デザイナが使えない

19ページ  
グリッドの画面を作ってみるというところで、ここはデザイナを使ってみるか、と思ったわけですが。  
Xamarin.formsのデザイナは提供されていない？

しかし、こんなページもあるので、ないことはないのでは？？  
<a title="https://docs.microsoft.com/ja-jp/visualstudio/designers/creating-a-ui-by-using-xaml-designer-in-visual-studio?view=vs-2017" href="https://docs.microsoft.com/ja-jp/visualstudio/designers/creating-a-ui-by-using-xaml-designer-in-visual-studio?view=vs-2017" target="_blank" rel="noopener noreferrer">https://docs.microsoft.com/ja-jp/visualstudio/designers/creating-a-ui-by-using-xaml-designer-in-visual-studio?view=vs-2017</a>

Blendならもしかしたら、と思いさらに頑張って10GB空けてインストールしたが、そもそもXamarinのテンプレートがない。  
<a href="https://marketplace.visualstudio.com/items?itemName=mohamedalinouira.XamarinFormsTemplates" target="_blank" rel="noopener noreferrer">https://marketplace.visualstudio.com/items?itemName=mohamedalinouira.XamarinFormsTemplates</a>  
をインストールしてみるがダメ。

[https://developercommunity.visualstudio.com/content/problem/272117/xamarin-designer-not-working.html][1]  
を見てアルファ版のフィックスも入れてみたがダメ。

よくよく見てみると、デザイナの説明は、Xamarinの説明ではない！  
Windowsユニバーサルとか、デスクトップアプリケーションをxamlで作る場合はデザイナが使えるけど、xamarinのxamlではデザイナは使えないというお話でした。

プレビュー機能は提供されているので、こんな感じになります。

[<img style="margin: 0px; display: inline; background-image: none;" title="image" src="/uploads/2018/10/image_thumb-2.png?resize=244%2C132&#038;ssl=1" alt="image" width="244" height="132" border="0" data-recalc-dims="1" />][2]

この画面でいうと、左側のxml記述に、一番左のツールボックスからドラッグアンドドロップはできます。  
これで頑張るしかないのですね。

なお、Windowsユニバーサルの方で作成したXamlからコピペできるかなと思ったら、色々違うようでそれもできず。

厳しい！

 [1]: https://developercommunity.visualstudio.com/content/problem/272117/xamarin-designer-not-working.html "https://developercommunity.visualstudio.com/content/problem/272117/xamarin-designer-not-working.html"
 [2]: /uploads/2018/10/image-2.png?ssl=1