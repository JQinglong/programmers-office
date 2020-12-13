---
title: Google API
type: post
date: 2010-01-03T04:18:50+00:00
url: /google-api/
post_views_count:
  - 186

---
ということで、リハビリ。  
<a href="http://konnokiyotaka.txt-nifty.com/pgblog/2009/12/devlove9010.html" target="_blank">DevLOVE2009でもらった</a><a href="http://hb.afl.rakuten.co.jp/hgc/06d13246.10ebaa62.06d13247.1eb85ca0/?pc=http%3A%2F%2Fsearch.books.rakuten.co.jp%2Fbksearch%2Fdt%3Fg%3D001%26bisbn%3D477414004X" target="_blank">WEB+DB PRESS Vol.53 </a>。  
久しぶりに読んだのですが、かなり骨太ですね。やはり、こういうのを読み続けないといかんと、反省させられます。  
一番面白かったのは、Google APIの記事。  
久しぶりに仕事以外のコードを書いた気がしますが、getElementByIdをgetElementByIDと書いてしばらくはまるという体たらく。  
こういうのは基礎体力というか、間違ってはいけないんですよね。どんなにテストやデバッグがよくできても、それはやらなくても良いことを上手にやってるみたいな。  
気を取り直して、こんなコードが紹介されていました。  
<script type=<span style="color:#009900;">"text/javascript"</span> src=<span style="color:#009900;">"http://www.google.com/jsapi"</span>></script>  
<script type = <span style="color:#009900;">"text/javascript"</span>>  
google.load(<span style="color:#009900;">"search"</span>,<span style="color:#009900;">"1"</span>);  
google.setOnLoadCallback(<span style="color:#000099;">function</span>(){  
<span style="color:#990000;">//検索コンロトールオブジェクトの作成</span>  
<span style="color:#000099;">var</span> searchControl = <span style="color:#000099;">new</span> google.search.SearchControl();  
searchControl.addSearcher(<span style="color:#000099;">new</span> google.search.WebSearch());  
searchControl.addSearcher(<span style="color:#000099;">new</span> google.search.ImageSearch());  
<span style="color:#990000;">//検索コントロールをHTMLとして描画</span>  
searchControl.draw(document.getElementById(<span style="color:#009900;">"search"</span>));  
<span style="color:#990000;">//初期検索</span>  
searchControl.execute(<span style="color:#009900;">"検索したい文字"</span>);  
});  
</script>  
そうするとこんな表示がされます。

<div id="search">
</div>

いい感じですね。  
他にもやってみたいものが一杯です。  
是非色々試してみましょう。 

<table>
  <tr>
    <td style="vertical-align: top;">
      <a href="http://hb.afl.rakuten.co.jp/hgc/06d13246.10ebaa62.06d13247.1eb85ca0/?pc=http%3A%2F%2Fsearch.books.rakuten.co.jp%2Fbksearch%2Fdt%3Fg%3D001%26bisbn%3D477414004X" target="_blank"> <img src="https://i2.wp.com/ecx.images-amazon.com/images/I/61BPPczjIXL._SL160_.jpg" style="border-style: none;" data-recalc-dims="1" /> </a>
    </td>
    <td style="vertical-align: top;">
      <a href="http://hb.afl.rakuten.co.jp/hgc/06d13246.10ebaa62.06d13247.1eb85ca0/?pc=http%3A%2F%2Fsearch.books.rakuten.co.jp%2Fbksearch%2Fdt%3Fg%3D001%26bisbn%3D477414004X" target="_blank"> WEB+DB PRESS Vol.53 </a><br /> <a href="http://www.amazon.co.jp/WEB-DB-PRESS-Vol-53-PRESS%E7%B7%A8%E9%9B%86%E9%83%A8/dp/477414004X%3FSubscriptionId%3D1JWQWN8E4Z5TR27962G2%26tag%3Dgaeaffibook-22%26linkCode%3Dxm2%26camp%3D2025%26creative%3D165953%26creativeASIN%3D477414004X" target="_blank"> Amazonで購入 </a><br /> <a href="http://px.a8.net/svt/ejp?a8mat=1HPMBD+EAZZ1U+5WS+C1DUQ&a8ejpredirect=http%3A%2F%2Fsearch.books.rakuten.co.jp%2Fbksearch%2Fdt%3Fg%3D001%26bisbn%3D477414004X" target="_blank">楽天ブックスで購入[楽天スーパーポイント発生]</a> <img src="https://i2.wp.com/www12.a8.net/0.gif?resize=1%2C1" alt="" width="1" border="0" height="1" data-recalc-dims="1" /><br /> <a href="http://px.a8.net/svt/ejp?a8mat=1HRMFS+EEKKOI+10UY+HUKPU&a8ejpredirect=http%3A%2F%2Fwww.bk1.jp%2FkeywordSearchResult%2F%3Fkeyword%3D477414004X%26storeCd%3D1%26searchFlg%3D9%26x%3D43%26y%3D11%26partnerid%3D02a801" target="_blank">ビーケーワン（ｂｋ１）で購入[コンビニ後払いあり]</a> <img src="https://i2.wp.com/www12.a8.net/0.gif?resize=1%2C1" alt="" width="1" border="0" height="1" data-recalc-dims="1" /><br /> <a href="http://click.linksynergy.com/fs-bin/statform?id=aR0TIOX*qAA&offerid=137560&bnid=1490&subid=&subid=0&kword_in=477414004X&oop=on" target="_blank">セブンアンドワイで購入[セブン-イレブン受取りなら送料０円]</a><img src="http://ad.linksynergy.com/fs-bin/show?id=aR0TIOX*qAA&bids=137560&type=5&subid=0" width="1" border="0" height="1" /><br /> <a href="http://click.linksynergy.com/fs-bin/statform?id=aR0TIOX*qAA&offerid=33310&bnid=2&subid=0&ifc=4&ifr=9784774140049" target="_blank">boopleで購入[100円で1ポイント]</a>
    </td>
  </tr>
  
  <tr>
    <td colspan="2">
      <div style="float: right;">
        <a href="http://affibook.appspot.com/" target="_blank">AffiBook!!</a>
      </div>
    </td>
  </tr>
</table>

<p class="scribefire-powered">
  Powered by <a href="http://www.scribefire.com/">ScribeFire</a>.
</p>

<div class="zemanta-pixie">
  <img class="zemanta-pixie-img" alt="" src="https://i1.wp.com/img.zemanta.com/pixy.gif" data-recalc-dims="1" />
</div>