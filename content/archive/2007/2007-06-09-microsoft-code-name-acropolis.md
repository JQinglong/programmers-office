---
title: Microsoft code name "Acropolis"
type: post
date: 2007-06-09T02:07:01+00:00
archives:
    - 2007
url: /microsoft-code-name-acropolis/
post_views_count:
  - 80

---
[Microsoft code name &#8220;Acropolis&#8221; &#8211; WindowsClient.net][1]

画面デザインって、その組織によって傾向があるのではないかと思います。  
うちの会社も、今はフレームワーク準拠なので当たり前ですが、その前のAccessでやっていたころでも、人によって配色パタンが違ったりはするものの、基本的なつくりはよく似ていました。  
しかし、「よく似ている」と「パタン化されている」は別物でして、

[UIデザインパターン][2]

のように、例えば2ペインでも4パタンくらい考えられて、どれかに当てはめましょう、とやっていたらちょっと違った世界があったのかと思います。

さて、Microsoft code name &#8220;Acropolis&#8221; 。こちらの記事も。  
[【TechEd 2007】マイクロソフト製の業務用ソフト開発コンポーネント群「Acropolis」が登場：ITpro][3]

<a href="http://konnokiyotaka.txt-nifty.com/pgblog/2007/05/post_d8ff.html" target="_blank">ちょっと前にも書きましたが</a>、画面デザインはこれから難しくなってくるだろうと言わざるを得ないわけで、それに対応するために規約を作るのもよいのですが、規約に合致していることのテストというのはなかなか難しいわけです。  
そうではなく、すなわち、規約を人間に守らせるアプローチではなく、これを使ってくれれば楽にいいものが作れますよ、勝手に規約にも従ってますよ、というのがAcropolisのアプローチだと思います。それができるところはそうしないと。規約を作る人は、その規約をツール化できるかを考えないと。

ちなみに、上のITproで一点誤解しそうなところが。  
まるで写真4のような2ペイン画面ができそうに見えますが（最初そう思いました）、これはデザインの設定画面であり、これを実行すると下のような画面が表示されます。  
<a href="https://i2.wp.com/jqinglong.html.xdomain.jp/bimg/image_1.png" atomicselection="true"><img style="border-right: 0px; border-top: 0px; border-left: 0px; border-bottom: 0px" height="186" alt="image" src="https://i0.wp.com/jqinglong.html.xdomain.jp/bimg/image_thumb_1.png?resize=240%2C186" width="240" border="0" data-recalc-dims="1" /></a>&nbsp;  
いくつかサンプルがついてきますが、これをもとにしているのでこんな感じです。  
Notepad  
<a href="https://i1.wp.com/jqinglong.html.xdomain.jp/bimg/image_2.png" atomicselection="true"><img style="border-right: 0px; border-top: 0px; border-left: 0px; border-bottom: 0px" height="190" alt="image" src="https://i1.wp.com/jqinglong.html.xdomain.jp/bimg/image_thumb_2.png?resize=240%2C190" width="240" border="0" data-recalc-dims="1" /></a>  
RSSEagle  
<a href="https://i0.wp.com/jqinglong.html.xdomain.jp/bimg/image_3.png" atomicselection="true"><img style="border-right: 0px; border-top: 0px; border-left: 0px; border-bottom: 0px" height="148" alt="image" src="https://i1.wp.com/jqinglong.html.xdomain.jp/bimg/image_thumb_3.png?resize=240%2C148" width="240" border="0" data-recalc-dims="1" /></a> 

インストール後に表示されるメッセージで、こちらもどうぞとなっているのですが、ようするにこのような画面をXAMLで作っておいて、Ｗｅｂ画面にもできますよということですかね。これはまた後でということで。  
[XAML to HTML Conversion Demo][4]

 [1]: http://windowsclient.net/Acropolis/
 [2]: http://www.sociomedia.co.jp/category/uidesignpatterns/
 [3]: http://itpro.nikkeibp.co.jp/article/NEWS/20070608/274077/
 [4]: http://msdn2.microsoft.com/en-us/library/aa972129.aspx