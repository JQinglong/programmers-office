---
title: '[vsug2009summer]Azure開発'
type: post
date: 2009-06-07T16:15:48+00:00
url: /vsug2009summerazure開発/
post_views_count:
  - 910

---
お父さんたちも「やっぱクラウドだよね」なんて盛り上がってしまう今日、ぜひAzureもやっておかないとね。

イベント直前に知ったのですが、イベントでも宣伝されていたこんな企画があります。  
<a href="http://www.newcloudapp.com/" target="_blank">new CloudApp() &#8211; The Azure™ Services Platform Developer Challenge</a>  
<a href="http://blogs.msdn.com/tsmatsuz/archive/2009/06/05/info-new-cloudapp-azure-services-platform.aspx" target="_blank">[Info] new CloudApp() ~ Azure Services Platform 開発コンテスト開催</a>

ちょっと勘違いしていましたが、Azureって僕らも使っていいんですね。現在はCTPということで。で、秋くらいに価格とかSLAとかが決まってくるんですね。  
[http://internet.watch.impress.co.jp/cda/event/2009/01/27/22229.html][1]

ということで、環境を作り始めます。以下の二つが役に立ちます。  
<a href="http://d.hatena.ne.jp/dotwow/20090514" target="_blank">WindowsAzure　勉強　１ &#8211; dotwow開発日記</a>  
[Azure Services Platform まだCTPだけど開発環境を作ってみる &#8211; Windows Live][2]  
前者は申請系、後者はインストール系、特に後者のIISの設定に助けられました。何で設定場所を違うところにしたんですかね・・・！

<table>
  <tr>
    <td style="vertical-align: top">
      <a href="http://www.amazon.co.jp/%E3%82%AF%E3%83%A9%E3%82%A6%E3%83%89%E3%81%AE%E8%A1%9D%E6%92%83%E2%80%95%E2%80%95IT%E5%8F%B2%E4%B8%8A%E6%9C%80%E5%A4%A7%E3%81%AE%E5%89%B5%E9%80%A0%E7%9A%84%E7%A0%B4%E5%A3%8A%E3%81%8C%E5%A7%8B%E3%81%BE%E3%81%A3%E3%81%9F-%E9%87%8E%E6%9D%91%E7%B7%8F%E5%90%88%E7%A0%94%E7%A9%B6%E6%89%80-%E5%9F%8E%E7%94%B0-%E7%9C%9F%E7%90%B4/dp/4492580824%3FSubscriptionId%3D1JWQWN8E4Z5TR27962G2%26tag%3Dgaeaffibook-22%26linkCode%3Dxm2%26camp%3D2025%26creative%3D165953%26creativeASIN%3D4492580824" target="_blank"><img style="border-bottom-style: none; border-right-style: none; border-top-style: none; border-left-style: none" src="https://i2.wp.com/ecx.images-amazon.com/images/I/41NQuCvoPYL._SL160_.jpg" data-recalc-dims="1" /> </a>
    </td>
    <td style="vertical-align: top">
      <a href="http://www.amazon.co.jp/%E3%82%AF%E3%83%A9%E3%82%A6%E3%83%89%E3%81%AE%E8%A1%9D%E6%92%83%E2%80%95%E2%80%95IT%E5%8F%B2%E4%B8%8A%E6%9C%80%E5%A4%A7%E3%81%AE%E5%89%B5%E9%80%A0%E7%9A%84%E7%A0%B4%E5%A3%8A%E3%81%8C%E5%A7%8B%E3%81%BE%E3%81%A3%E3%81%9F-%E9%87%8E%E6%9D%91%E7%B7%8F%E5%90%88%E7%A0%94%E7%A9%B6%E6%89%80-%E5%9F%8E%E7%94%B0-%E7%9C%9F%E7%90%B4/dp/4492580824%3FSubscriptionId%3D1JWQWN8E4Z5TR27962G2%26tag%3Dgaeaffibook-22%26linkCode%3Dxm2%26camp%3D2025%26creative%3D165953%26creativeASIN%3D4492580824" target="_blank">クラウドの衝撃――IT史上最大の創造的破壊が始まった </a><br />野村総合研究所 城田 真琴<br />おすすめ度:4.0<br />レビュー件数:21<br /><a href="http://www.amazon.co.jp/%E3%82%AF%E3%83%A9%E3%82%A6%E3%83%89%E3%81%AE%E8%A1%9D%E6%92%83%E2%80%95%E2%80%95IT%E5%8F%B2%E4%B8%8A%E6%9C%80%E5%A4%A7%E3%81%AE%E5%89%B5%E9%80%A0%E7%9A%84%E7%A0%B4%E5%A3%8A%E3%81%8C%E5%A7%8B%E3%81%BE%E3%81%A3%E3%81%9F-%E9%87%8E%E6%9D%91%E7%B7%8F%E5%90%88%E7%A0%94%E7%A9%B6%E6%89%80-%E5%9F%8E%E7%94%B0-%E7%9C%9F%E7%90%B4/dp/4492580824%3FSubscriptionId%3D1JWQWN8E4Z5TR27962G2%26tag%3Dgaeaffibook-22%26linkCode%3Dxm2%26camp%3D2025%26creative%3D165953%26creativeASIN%3D4492580824" target="_blank">Amazonで購入[15ポイント発生] </a></p>
      <p>
        <a href="http://px.a8.net/svt/ejp?a8mat=1HPMBD+EAZZ1U+5WS+C1DUQ&a8ejpredirect=http%3A%2F%2Fsearch.books.rakuten.co.jp%2Fbksearch%2Fdt%3Fg%3D001%26bisbn%3D4492580824" target="_blank">楽天ブックスで購入[楽天スーパーポイント発生]</a> <img border="0" alt="" src="https://i2.wp.com/www12.a8.net/0.gif?resize=1%2C1" width="1" height="1"  data-recalc-dims="1" /><br /><a href="http://px.a8.net/svt/ejp?a8mat=1HRMFS+EEKKOI+10UY+HUKPU&a8ejpredirect=http%3A%2F%2Fwww.bk1.jp%2FkeywordSearchResult%2F%3Fkeyword%3D4492580824%26storeCd%3D1%26searchFlg%3D9%26x%3D43%26y%3D11%26partnerid%3D02a801" target="_blank">ビーケーワン（ｂｋ１）で購入[コンビニ後払いあり]</a> <img border="0" alt="" src="https://i2.wp.com/www12.a8.net/0.gif?resize=1%2C1" width="1" height="1"  data-recalc-dims="1" /><br /><a href="http://click.linksynergy.com/fs-bin/statform?id=aR0TIOX*qAA&offerid=137560&bnid=1490&subid=&subid=0&kword_in=4492580824&oop=on" target="_blank">セブンアンドワイで購入[セブン-イレブン受取りなら送料０円]</a><img border="0" src="http://ad.linksynergy.com/fs-bin/show?id=aR0TIOX*qAA&bids=137560&type=5&subid=0" width="1" height="1" /><br /><a href="http://click.linksynergy.com/fs-bin/statform?id=aR0TIOX*qAA&offerid=33310&bnid=2&subid=0&ifc=4&ifr=9784492580820" target="_blank">boopleで購入[100円で1ポイント]</a></td> </tr> 
        
        <tr>
          <td colspan="2">
            <div style="float: right">
              <a href="http://affibook.appspot.com/" target="_blank">AffiBook!!</a>
            </div>
          </td>
        </tr></tbody> </table>

 [1]: http://internet.watch.impress.co.jp/cda/event/2009/01/27/22229.html "http://internet.watch.impress.co.jp/cda/event/2009/01/27/22229.html"
 [2]: http://kame-taro.spaces.live.com/blog/cns!CD806281181610EF!766.entry