---
title: Code4StartUp ～ UberEatsを作ろう ～ Python/Django環境
author: KONNO Kiyotaka
type: post
date: 2018-05-03T00:31:24+00:00
archives:
    - 2018
url: /code4startup-～-ubereatsを作ろう-～-python-django環境/
post_views_count:
  - 1077
categories:
  - プログラミング
tags:
  - Code4Startup

---
次は、Webアプリ側の環境で、Djangoです。

もう、これは、最初からCloud9で楽勝でしょう、と思っていたら甘かった・・・

### AWS Cloud9とは

　元々Cloud9を使用しており、開発環境をワンクリックで簡単に構築できることが売りだったので、それでよいやと思っていたわけです。  
　ただ、昨年AWSに統合されたバージョンがリリースされました。最初は旧版とAWS版並列で行くていくのかなと思っていたのですが、どうやら移行を促されるようなので、この機会にAWS版を使用することにしました。

（旧版は新規プロジェクト作成時は、こんな感じでテンプレートを選択できます。ボタンを押すだけで、すぐに開発環境ができあがり、ソースを書き始めることができます。）  
[<img width="244" height="102" title="image" style="margin: 0px; display: inline; background-image: none;" alt="image" src="/uploads/2018/05/image_thumb-4.png?resize=244%2C102&#038;ssl=1" border="0" data-recalc-dims="1" />][1]

　いざ使おうとすると、色々分かってきます。  
　まず、AWS Cloud9は、IDEとしては無償なのですが、環境とセットにはなっていません。  
　分かりにくいですが、他のサーバを使用してSSHで接続するか、AWSのEC2に乗せる必要があります。すなわち、環境自体は無償とは限らないということです。  
　EC2も12か月間は無償利用できるというのがアピールされていますが、1年後にどうするか悩むことになるのであれば、そこには頼りたくないなという気持ちがわきました。  
　選択肢として、たまたま最近さくらレンタルサーバを契約したので、それでもよいかと思ったのですが、それだと世間の人にとっては無償でもなんでもなくなりますし、そちらは今あまり壊したくないというのもありました。  
　そこで他の選択肢を探し、見つけたのがGCE（Google Compute Engine）でした。

### GCE（Google Compute Engine）を使用する

　GCEは、最初にOSやCPU等を選択して、まっさらのOS環境が提供される、という意味で、レンタルサーバとほぼ同様と考えてよいかと思います。  
　とはいえ最低限のものは入っていると予想して、設定を開始します。今回必要なのはPython3でDjangoを動かすことです。  
　ここで頭の中に持っておいた方が良いと思うことは、Cloud9（AWS）側の設定と、GCEの設定がある、ということです。そして、ほとんどの作業はGCE側の設定です。Cloud9の画面を見ていますが、それはGCEに接続して作業しているということです。

　話がいったんAWS Cloud9に戻りますが、新規プロジェクト作成時に、ワンクリックで環境設定してくれる、という機能はなくなってしまいました。繰り返しますが、あくまでもIDEです。ですから、SSHで接続した後は、必要なインストール作業を行う必要があります。IDEの中にターミナル機能が統合されている等は旧版と同じですので、そこで以下の作業を行います。

　まず、Cloud9側でPython3を選択します。けど、これは要はIDEの設定であり、環境の設定ではありません。  
　では、ということで、ここからCode4StartUpのビデオを見ながら環境を作っていこうと思います。  
　そしていきなり躓きます。「sudo apt-get install python3-venv」ができません。以下失敗なので、簡単に流しますが、python3.4-venvなら成功しますが、ビデオの後の方で3.5であることを確認されますので、やばい、3.5にあげないと、と思います。Cloud9の画面では「/usr/local/lib/python2.7/dist-packages:/usr/local/lib/python3.4/dist-packages:/usr/local/lib/python3.5/dist-packages」と書いてあるのに何でないのだ？と思っていたましたが、これはあくまでもIDEの設定です。環境は別です。  
　色々調べて、「sudo python -m pip install &#8211;upgrade pip」しようとしますが、ないと言われます。色々あって、3.5ではなく最新の3.6でよいやと思い「sudo add-apt-repository ppa:jonathonf/python-3.6」以下・・・（省略）でインストールします、しかし、「python3.6 &#8211;version」では3.6インストールが確認できますが、「python3 &#8211;version」ではまだ3.4を参照しています。  
　そこで、pyenvというものの存在に出会い、「curl -L https://raw.githubusercontent.com/pyenv/pyenv-installer/master/bin/pyenv-installer | bash」でインストールしようとしますが、gitが入っていない、とのエラー。なんと！そこからですか！  
　gitインストールしてから再度pyenvインストールして、それでも「pyenv install &#8211;list」で表示されないので「sudo apt-get install -y make build-essential libssl-dev zlib1g-dev libbz2-dev libreadline-dev libsqlite3-dev wget curl llvm libncurses5-dev libncursesw5-dev xz-utils」して、「pyenv install 3.6.3」しようとすると、画面が返ってこなくなります。  
　本当はもう3.6.3入っているからね、と、ここで心が折れて、VMをいったん削除して、再度作り直して、今度はpyenvで最初からインストールするぞ、としようと思ったのでした。

　**衝撃の結末**

　としか、言いようがありません。  
　今度はgitは既に入っていました。pyenvはインストールして、そういえば、と「python3 &#8211;version」を確認したら、なんと、3.5.2。できた。というか、できてた。

　何が違ったんだろう。謎でしかありません。  
　とりあえず、この環境で、進められ、Djangoも無事動いているように見えますが、普通に起動すると127.0.0.1で動きます。外部アドレスに置き換えてみると接続できませんでした。開発環境的には大丈夫だと思いますが、この辺も旧Cloud9ではうまくしてくれていた部分なので、ちょっと歯がゆいなと思います。

（追記）  
<a href="https://cloud.google.com/python/django/container-engine?hl=ja" target="_blank">Container Engine での Django の実行</a>  
これを全部やれと？ぞっとします・・・  
↓  
そんなことはありませんでした。GCPのファイアウォールの設定でtcp8000を許可すれば、外部アドレスで参照可能となりました。  
ただし、サービス起動は「python manage.py runserver」ではダメで「python manage.py runserver 内部アドレス:8000」とする必要があります。

 [1]: /uploads/2018/05/image-4.png?ssl=1