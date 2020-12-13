---
title: Code4StartUp ～ UberEatsを作ろう ～ Swift環境
author: KONNO Kiyotaka
type: post
date: 2018-05-02T02:15:27+00:00
url: /code4startup-～-ubereatsを作ろう-～-swift環境/
post_views_count:
  - 1139
categories:
  - プログラミング
tags:
  - Code4Startup

---
<a href="https://code4startup.com/?ref=kiyotakakonno" target="_blank" rel="noopener">Code4Startup</a>

こちらが本題の、UberEatsを作ろう（Create UberEats with Python/Django and Swift 3）。

まずは、環境構築から始まるのですが、Python、Heroku、Atomは使用するしないは良いとして、XcodeはWindows環境だとどうしようもない。

しかし、今の時代、色々な方法はあるようで、Swiftのためだけなら、Xcodeがなくても何とかなるっぽい。

ということで、環境作ってみました。

### IBM Swift Sandboxはもう存在しない？

まず、最初に、「IBM Swift Sandbox」というものが気になりましたが、現在はリンク切れです。  
ただ、もう少し粘ってみると、<a href="https://console.bluemix.net/developer/appservice/dashboard?cm_sp=dw-bluemix-_-swift-_-devcenter" target="_blank" rel="noopener">IBM Cloud App Service</a> というものに誘導されます。  
こちらを登録すると、開発環境も使えるようになるのですが、その言語がSwiftになっています。  
（いろいろなタイプが選べますが、一番左上の「プロジェクトの作成」を選ぶとswiftになるのです。）  
[<img style="margin: 0px; display: inline; background-image: none;" title="image" src="https://i1.wp.com/www.programmers-office.ml/wp-content/uploads/2018/05/image_thumb.png?resize=244%2C206&#038;ssl=1" alt="image" width="244" height="206" border="0" data-recalc-dims="1" />][1]

[<img style="margin: 0px; display: inline; background-image: none;" title="image" src="https://i2.wp.com/www.programmers-office.ml/wp-content/uploads/2018/05/image_thumb-1.png?resize=244%2C210&#038;ssl=1" alt="image" width="244" height="210" border="0" data-recalc-dims="1" />][2]

けど、より簡単なのは、Swift Kituraを選択することのようです。  
[<img style="margin: 0px; display: inline; background-image: none;" title="image" src="https://i1.wp.com/www.programmers-office.ml/wp-content/uploads/2018/05/image_thumb-2.png?resize=199%2C244&#038;ssl=1" alt="image" width="199" height="244" border="0" data-recalc-dims="1" />][3]

しかし、いずれにせよ、Swift Sandboxで企図されていたようなものではないようです。その場でソースを書いて実行するのであればよかったのですが、あくまでもローカルでソースを書くのであれば、ちょっと必要性が薄いかなと。  
こちらは、いったん中断しておきます。

### ローカルにSwift環境を構築

ですので、ローカルに環境を構築することにします。  
基本的には、  
[https://qiita.com/akira_/items/e5550dbb571a20deb3c1][4]  
を参考にさせていただきました。

Windows Subsystem for Linux、知りませんでした。  
途中再起動等入るのと、これを有効にした後に、Linuxパッケージを導入する、というところに注意です。  
[<img style="margin: 0px; display: inline; background-image: none;" title="image" src="https://i1.wp.com/www.programmers-office.ml/wp-content/uploads/2018/05/image_thumb-3.png?resize=244%2C191&#038;ssl=1" alt="image" width="244" height="191" border="0" data-recalc-dims="1" />][5]  
Windowsでこんな選択画面を表示する、ということ自体驚きですが、いかがでしょうか。

その後は、インストールされたUbuntuバージョンに合わせて、記述を調整しながら進めれば、環境構築完了し、Hello worldまでは行けました。

なお、元々Git Bashが入っていた環境ですので、バッティング等も気にならないでもないですが、とりあえずどちらも動いています。

### （2018年10月）結局MAC購入

# [Code4StartUp ～ UberEatsを作ろう ～ iMac購入して続行][6] {.post-title}

結局、iOSアプリ作ろうと思ったら買わざるを得ませんでした・・・

&nbsp;

<a href="https://code4startup.com/?ref=kiyotakakonno" target="_blank" rel="noopener">Code4Startup</a>

 [1]: https://i2.wp.com/www.programmers-office.ml/wp-content/uploads/2018/05/image.png?ssl=1
 [2]: https://i2.wp.com/www.programmers-office.ml/wp-content/uploads/2018/05/image-1.png?ssl=1
 [3]: https://i0.wp.com/www.programmers-office.ml/wp-content/uploads/2018/05/image-2.png?ssl=1
 [4]: https://qiita.com/akira_/items/e5550dbb571a20deb3c1 "https://qiita.com/akira_/items/e5550dbb571a20deb3c1"
 [5]: https://i2.wp.com/www.programmers-office.ml/wp-content/uploads/2018/05/image-3.png?ssl=1
 [6]: https://www.programmers-office.ml/2018/10/28/code4startup-%ef%bd%9e-ubereats%e3%82%92%e4%bd%9c%e3%82%8d%e3%81%86-%ef%bd%9e-imac%e8%b3%bc%e5%85%a5%e3%81%97%e3%81%a6%e7%b6%9a%e8%a1%8c/