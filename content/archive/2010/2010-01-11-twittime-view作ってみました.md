---
title: Twittime View作ってみました
type: post
date: 2010-01-11T13:24:58+00:00
archives:
    - 2010
url: /twittime-view作ってみました/
post_views_count:
  - 84

---
いや、本当に申し訳ないです（分かる人だけ）。何かの罠です。はぁ・・・びっくりした・・・

ということで、こんなものを作りました。  
Twitterの検索結果をタイムラインで見るというものです。

（あえて踏み込みますが）今日だと岸良さんがいい感じです。  
<a target="_blank" href="http://twittimeview.appspot.com/?keyword=%E5%B2%B8%E8%89%AF">http://twittimeview.appspot.com/?keyword=%E5%B2%B8%E8%89%AF</a>

このためのテストデータだったという説も（悔やんでも悔やみきれない）。

（気を取り直して）解説  
<a target="_blank" href="http://konnokiyotaka.txt-nifty.com/pgblog/2010/01/google-visualiz.html">Google Visualization API</a>面白かったので以前から自分の中で一つのテーマにしているタイムラインを作ってみようと思ったのですが、有りあわせのものではやはり限界があり、サーバ側サービスだと微調整のために自分で直すと言うこともできず、いったんあきらめかけました。  
しかし、これだけjavascriptの世界が進んであるのであれば、タイムラインを作るライブラリくらいあるだろうと言うことで、見つけたのがこちら。  
<a target="_blank" href="http://www.simile-widgets.org/">SIMILE Widgets</a>  
まさに今回のイメージにピッタリで、かつ使いやすい。ということで、サンプルをちょこっといじっただけで完了です（それなりに苦労はしましたが）。  
なお、本当は、Javascriptから直接Twitter APIにアクセスできたらサーバ側アプリもいらないかなと思ったのですが、いまいちJSONが分かっていないこともあり、サーバ側pythonで取得したXMLを整形して、Javascriptとしてデータ書き出しを行うという、ちょっとださい作り。HTMLソースを見てもらえば、どんなことをやっているかは分かると思います。  
データ取得に関してはこちらも参考にさせていただきました。  
<a target="_blank" href="http://wwww.vis.ne.jp/mt/2009/12/google_app_engine_twitter_api.html">http://wwww.vis.ne.jp/mt/2009/12/google_app_engine_twitter_api.html</a>

あまりTwitterには馴染めていないのですが、こんな見方はあっても良いですよね。  
アジアでは、<a href="http://www.plurk.com/" target="_blank">「Plurk（プラーク）」</a>がはやっているという話もあります。例えば人気歌手潘瑋柏さんのPlurkはこんな感じ。  
<a target="_blank" href="http://www.plurk.com/willpan">http://www.plurk.com/willpan</a>  
確かに、Lang-8でも半年以上前にこれがはやっていると言っていた中国人がいたんですよね。タイムラインという言葉にも馴染みますよね。

強いて言えば、ちょっと見える化されすぎる。まさに浮気もばれるかもしれないレベル。  
つぶやき過ぎにご用心。（それ以上に内容にご用心・・・; ;）

<table>
  <tr>
    <td style="vertical-align: top;">
      <a href="http://hb.afl.rakuten.co.jp/hgc/06d13246.10ebaa62.06d13247.1eb85ca0/?pc=http%3A%2F%2Fsearch.books.rakuten.co.jp%2Fbksearch%2Fdt%3Fg%3D001%26bisbn%3D4806128953" target="_blank"> <img src="https://i0.wp.com/ecx.images-amazon.com/images/I/51JpzOIuLlL._SL160_.jpg" style="border-style: none;" data-recalc-dims="1" /> </a>
    </td>
    <td style="vertical-align: top;">
      <a href="http://hb.afl.rakuten.co.jp/hgc/06d13246.10ebaa62.06d13247.1eb85ca0/?pc=http%3A%2F%2Fsearch.books.rakuten.co.jp%2Fbksearch%2Fdt%3Fg%3D001%26bisbn%3D4806128953" target="_blank"> 三方良しの公共事業改革 </a><br />岸良 裕司<br />おすすめ度:5.0<br />レビュー件数:5<br /><a href="http://www.amazon.co.jp/%E4%B8%89%E6%96%B9%E8%89%AF%E3%81%97%E3%81%AE%E5%85%AC%E5%85%B1%E4%BA%8B%E6%A5%AD%E6%94%B9%E9%9D%A9-%E5%B2%B8%E8%89%AF-%E8%A3%95%E5%8F%B8/dp/4806128953%3FSubscriptionId%3D1JWQWN8E4Z5TR27962G2%26tag%3Dgaeaffibook-22%26linkCode%3Dxm2%26camp%3D2025%26creative%3D165953%26creativeASIN%3D4806128953" target="_blank"> Amazonで購入 </a></p>
      <p>
        <a href="http://px.a8.net/svt/ejp?a8mat=1HPMBD+EAZZ1U+5WS+C1DUQ&a8ejpredirect=http%3A%2F%2Fsearch.books.rakuten.co.jp%2Fbksearch%2Fdt%3Fg%3D001%26bisbn%3D4806128953" target="_blank">楽天ブックスで購入[楽天スーパーポイント発生]</a> <img src="https://i2.wp.com/www12.a8.net/0.gif?resize=1%2C1" alt="" width="1" border="0" height="1" data-recalc-dims="1" /><br /><a href="http://px.a8.net/svt/ejp?a8mat=1HRMFS+EEKKOI+10UY+HUKPU&a8ejpredirect=http%3A%2F%2Fwww.bk1.jp%2FkeywordSearchResult%2F%3Fkeyword%3D4806128953%26storeCd%3D1%26searchFlg%3D9%26x%3D43%26y%3D11%26partnerid%3D02a801" target="_blank">ビーケーワン（ｂｋ１）で購入[コンビニ後払いあり]</a> <img src="https://i2.wp.com/www12.a8.net/0.gif?resize=1%2C1" alt="" width="1" border="0" height="1" data-recalc-dims="1" /><br /><a href="http://click.linksynergy.com/fs-bin/statform?id=aR0TIOX*qAA&offerid=137560&bnid=1490&subid=&subid=0&kword_in=4806128953&oop=on" target="_blank">セブンアンドワイで購入[セブン-イレブン受取りなら送料０円]</a><img src="http://ad.linksynergy.com/fs-bin/show?id=aR0TIOX*qAA&bids=137560&type=5&subid=0" width="1" border="0" height="1" /><br /><a href="http://click.linksynergy.com/fs-bin/statform?id=aR0TIOX*qAA&offerid=33310&bnid=2&subid=0&ifc=4&ifr=9784806128953" target="_blank">boopleで購入[100円で1ポイント]</a></td> </tr> 
        
        <tr>
          <td colspan="2">
            <div style="float: right;">
              <a href="http://affibook.appspot.com/" target="_blank">AffiBook!!</a>
            </div>
          </td>
        </tr></tbody> </table> 
        
        <div class="zemanta-pixie">
          <img class="zemanta-pixie-img" alt="" src="https://i1.wp.com/img.zemanta.com/pixy.gif" data-recalc-dims="1" />
        </div>
        <p class="scribefire-powered">
          Powered by <a href="http://www.scribefire.com/">ScribeFire</a>.
        </p>