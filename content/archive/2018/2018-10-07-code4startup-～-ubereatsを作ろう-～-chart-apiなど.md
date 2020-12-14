---
title: Code4StartUp ～ UberEatsを作ろう ～ Chart APIなど
author: KONNO Kiyotaka
type: post
date: 2018-10-07T08:25:00+00:00
archives:
    - 2018
url: /code4startup-～-ubereatsを作ろう-～-chart-apiなど/
post_views_count:
  - 971
categories:
  - プログラミング
tags:
  - Code4Startup

---
<a href="https://code4startup.com/?ref=kiyotakakonno" target="_blank">Code4Startup</a>

Task14までdone。

途中結構長い時間はまったのが、  
Order.objects.filter・・・  
とすればよいところを  
OrderSerializer(Order.objects.filter・・・  
としてしまったために、発生したエラー。

他からのコピペで無意識についてしまったわけですが、これを探りながらの他のバグにも気づいたし、まあよいか。

Task14ではレポート画面と言ことで、グラフを出力するために、  
<a href="http://www.chartjs.org/" target="_blank">Chart.js</a>  
を使います。

これはこれでよいなと思いますが、  
<a href="https://developers.google.com/chart/" target="_blank">Google Charts</a>  
もあるからね、とは思ってしまいます。

そして、いよいよTask15でPythonは終了となりますが、一つの山場と考えているStripe連携。

ここまで連休中に終わらわせておいて、Swiftに入りましょう。