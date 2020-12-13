---
title: Code4StartUp ～ UberEatsを作ろう ～ iMac購入して続行
author: KONNO Kiyotaka
type: post
date: 2018-10-28T14:30:32+00:00
url: /code4startup-～-ubereatsを作ろう-～-imac購入して続行/
post_views_count:
  - 1104
categories:
  - プログラミング
tags:
  - Code4Startup

---
<a href="https://code4startup.com/?ref=kiyotakakonno" target="_blank" rel="noopener">Code4Startup</a>

## iMac購入

一旦Xamarinを始めたわけですが、そして第一印象はさほど悪くもなかったのですが、結局iOS版を作成するためにはXcodeの入ったMacが必要になるということで、熟慮した結果（1日ほど）iMacを購入しました。

iMac MK462J/A 一体型 PC 27型 Retina 5K Late 2015 Core i5 6500 3.2GHz 24GB HDD1TB High Sierra 10.13

中古ですが全く中古感なし。それでいてメモリが標準8GBのところ24GBに増設されており、値段は標準新品より7万円位安い。  
12インチMacBookの整備品も魅力はありましたが、使用中のThinkPad T430sも全然現役で使えることと、値段も上記中古品ならあまり変わらなくなってしまうということで、ちょっとだけ贅沢品を買いました。  
快適そのものです。

## swift開始

ということで、すぐさまXcodeをインストールし、と思ったらOSアップデートが必要と言われたのでアップデートし、環境を整えました。  
ちなみに、エディタどうしようかと思い、Macのエディタを検索したらいまだにCotEditorとか上位に出てきて、ムムとなりましたが（以前Mac使ってた時にはCotEditor派でしたけど）、素直にAtomとVSCodeで悩んでVSCodeにしました。

始めてみると、やはりこのデザインツールは素晴らしい。ここまでサポートしてくれると、やる気の出方が違います。  
とりあえず4レッスンやってみてのハマりポイントは二つ。  
一つは、FoodTaskerMobile-Bridging-Header.hのファイルの場所。レッスンの中ではこれをLibディレクトリに移動するのですが、参照できませんというエラーになります。  
<del><br /> これを参照できる場所に戻しても良いのですが、やった対応は、プロジェクトのBuild SettingsのObjective-C Bridging Headerの記述を削除すること。これで、このエラーは解消しました。<br /> </del>  
（2018/11/04）  
さすがにこれはダメ。後で、self.revealViewControllerというところの参照ができなくなります。  
FoodTaskerMobile/Lib/FoodTaskerMobile-Bridging-Header.h  
とすることで正常動作になります。

もう一つは、画面遷移しても目的のページが表示されず、白いままになってしまうこと。これは、実はView Controllerのページが表示されていたのですが、なぜそうなるか。結論は、このコントローラに対しては、クラスSWRevealViewControllerを指定しなければならないのですが、それが漏れていたため。ビデオではちゃんと設定することになっているので、その部分で居眠りしていたかもしれません。  
ということで、基本的な画面の作り方と、遷移の仕方は完了。

ついでに言うと、レッスンで使用しているアイコンはどこかで手に入れられるのか？？謎。

<div>
  <a href="https://code4startup.com/?ref=kiyotakakonno" target="_blank" rel="noopener">Code4Startup</a>
</div>

<div>
</div>