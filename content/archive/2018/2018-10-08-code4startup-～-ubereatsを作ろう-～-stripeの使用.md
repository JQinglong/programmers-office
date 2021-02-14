---
title: Code4StartUp ～ UberEatsを作ろう ～ Stripeの使用
author: KONNO Kiyotaka
type: post
date: 2018-10-08T02:45:59+00:00
archives:
    - 2018
url: /code4startup-～-ubereatsを作ろう-～-stripeの使用/
post_views_count:
  - 1077
categories:
  - プログラミング
tags:
  - Code4Startup

---
<a href="https://code4startup.com/?ref=kiyotakakonno" target="_blank" rel="noopener">Code4Startup</a>

自作サービスの決済手段として何を使うか、PayPalは開発者にやさしいなと思っていましたが、Stripeも十分良さそうです。

<figure style="width: 244px" class="wp-caption alignnone">[<img style="display: inline; background-image: none;" title="image" src="/uploads/2018/10/image_thumb.png?resize=244%2C145&#038;ssl=1" alt="Stripe" width="244" height="145" border="0" data-recalc-dims="1" />][1]<figcaption class="wp-caption-text">トップメニューに「開発者」があり、このサービスの向き先が伺える</figcaption></figure>

ちなみに、日本のサービスで、申込・審査を行わずに利用できるサービスはあるでしょうか？？  
ちょっと違うんだよなーと思ってしまいます。  
もちろん、そういうビジネスはそれでありなのですが、違うビジネスが展開されないのはなぜだろう、ということです。

そして、PayPal。  
開発者向けサービスも充実しているし、無料でテストサイトでの決済を確認することもできるし、実際に運用する際の手数料も安いとは思いませんが（弱小サイトを前提とする場合）許容できるのではないかと思いますし、非常に使いやすいと思います。

<figure style="width: 244px" class="wp-caption alignnone">[<img style="margin: 0px; display: inline; background-image: none;" title="image" src="/uploads/2018/10/image_thumb-1.png?resize=244%2C122&#038;ssl=1" alt="paypal" width="244" height="122" border="0" data-recalc-dims="1" />][2]<figcaption class="wp-caption-text">PayPalも開発者にやさしい</figcaption></figure>

ただ、唯一最大の問題が、決済サービスをしようとするためにはpaypalの会員登録が必要ということ。  
私のように一度登録してしまっている人としては、そういうものだと分かって使うのでよいのですが、paypalに縁のなかった人がいきなり支払いを行おうとしたらpaypal会員登録から始まってしまうというのは、ちょっとハードル高いのではないかと思われます。

それに対して、Stripe。  
普通にクレジットカード情報を送信することにより（実際は端末にStripeのトークンが返されて、これをサービスに送信することで、サービスがそのトークンとサービスのAPIキーを紐づけて）決済されるので、違和感なしで決済完了できるということです。

なお、開発中のアプリでは、ユーザ認識にユーザトークンのやり取りをしているので、トークントークン言われて分からんわ、という感じになりそうですが（実際それを間違えて送信しているというコーディングミスをしたり）、冷静になれば特に問題はありません。

なお、開発者向けドキュメントの中でデモ機能が用意されていて、そこでダミーのカード情報を送信することによりStripeのトークンを取得できる（そして、それを使って開発サービスのテストができる）わけですが、講義の中で紹介されているURLは既に変わってしまっており、stripe docs→Payments→Stripe.js and Elements→Quickstart　（Card Element Quickstart）  
<a title="https://stripe.com/docs/stripe-js/elements/quickstart" href="https://stripe.com/docs/stripe-js/elements/quickstart" target="_blank" rel="noopener">https://stripe.com/docs/stripe-js/elements/quickstart</a>  
から利用できるようになっています。

これは、別件のWordpressからの決済でも使ってみたいと思います。

 [1]: /uploads/2018/10/image.png?ssl=1
 [2]: /uploads/2018/10/image-1.png?ssl=1