---
title: Code4StartUp ～ UberEatsを作ろう ～ cocoapods
author: KONNO Kiyotaka
type: post
date: 2018-11-10T12:14:55+00:00
url: /code4startup-～-ubereatsを作ろう-～-cocoapods/
post_views_count:
  - 800
categories:
  - プログラミング
tags:
  - Code4Startup

---
<a href="https://code4startup.com/?ref=kiyotakakonno" target="_blank" rel="noopener">Code4Startup</a>

さて、クレジットカード情報入力画面を作るにあたっては、cocoapodsなるものを導入するようです。

ターミナルで、sudo gem install cocoapodsを叩きます。  
ビデオでは1 gem installedであっさり終わっていましたが、私の環境では結構な量のインストールログが流れて、28 gem installed。そもそも、ターミナルを立ち上げるのさえ初めてというまっさら環境ですから、そんな感じなのでしょうか。

次にpod initによって、Podfileというファイルができますが、それをVisual Studio Codeで開いて保存したらファイル名が「Pod file」になっていた。まあまあの驚き（何かの操作ミスかとは思いますが、そんなミスする？？）。  
さらに、pod installすると、ビデオではすぐにStripeのインストールが始まっていますが、私の環境では、Analyzing dependenciesから始まって、結構な量の何かをインストールし始めて、ちょっと不安になりましたが、無事完了。

そして、これをインストールすることにより、Viewにクラスを指定するだけで、クレジットカード番号入力欄が勝手にでき上がるというのはセンス良い！

という訳で、この辺も飛ばさずにやっておくべきですね。

<a href="https://code4startup.com/?ref=kiyotakakonno" target="_blank" rel="noopener">Code4Startup</a>