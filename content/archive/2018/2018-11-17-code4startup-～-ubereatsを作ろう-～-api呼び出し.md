---
title: Code4StartUp ～ UberEatsを作ろう ～ API呼び出し
author: KONNO Kiyotaka
type: post
date: 2018-11-17T01:07:21+00:00
url: /code4startup-～-ubereatsを作ろう-～-api呼び出し/
post_views_count:
  - 842
categories:
  - プログラミング
tags:
  - Code4Startup

---
<a href="https://code4startup.com/?ref=kiyotakakonno" target="_blank" rel="noopener">Code4Startup</a>

先に作ったFacebook連携用APIの呼び出し。

ここでログイン・ログアウトの機構を一気に作るので、ここをやっておかないとドライバー用アプリが進められなくなる。

が、とりあえず、一旦は一通りビデオを見てみることにする。

この先は、その他API呼び出しの部分なので、ある意味飛ばしても良いはず。

一つへーと思ったのは、API呼び出しで、httpだと怒られる訳ですが、info.plistで、App Transport Security Settingsの設定を追加することで接続できるようになる。  
例えば、この辺の情報ですね。  
<a href="https://qiita.com/uhooi/items/68939999c2c31e5f5557" target="_blank" rel="noopener">https://qiita.com/uhooi/items/68939999c2c31e5f5557</a>

&nbsp;