---
title: Code4StartUp ～ UberEatsを作ろう ～ Postmanのはまりポイント
author: KONNO Kiyotaka
type: post
date: 2018-10-01T13:04:47+00:00
url: /code4startup-～-ubereatsを作ろう-～-postmanのはまりポイント/
post_views_count:
  - 1097
categories:
  - プログラミング
tags:
  - Code4Startup

---
[Code4Startup][1]

Task11で、27分の長丁場のレッスンがあります。

いったん全部見てから、書いてみたのですが、途中ではまりました。

「AccessToken matching query does not exist.」

これは、結構な人がはまっているようなのですが、なかなかまともな回答がついていないように思われます。

正しい回答はこちら。

[https://uploads.disquscdn.com/images/bcf707b4c65186dcfcc293547fc57bbae63e2fa0fbddc89aa6b82dbdb7418f69.png][2]

Postmanのパラメータ指定時に、Body→form-dataを指定する必要があります。

そうしないと、request.POST.get(&#8220;access_token&#8221;)がNoneになってしまうのでした。

改めて、ビデオを見返すと、ちゃんと説明してくれてますなぁ＞＜

そして、同じ質問が、teratailに上がっていたので、初めて回答してみました。



もう少し飛ばしていきたいのですが、必ずどこかではまりますね・・・

 [1]: https://code4startup.com/?ref=kiyotakakonno
 [2]: https://uploads.disquscdn.com/images/bcf707b4c65186dcfcc293547fc57bbae63e2fa0fbddc89aa6b82dbdb7418f69.png "https://uploads.disquscdn.com/images/bcf707b4c65186dcfcc293547fc57bbae63e2fa0fbddc89aa6b82dbdb7418f69.png"