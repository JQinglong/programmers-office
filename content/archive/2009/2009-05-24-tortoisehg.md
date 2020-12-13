---
title: TortoiseHG
type: post
date: 2009-05-24T08:31:29+00:00
url: /tortoisehg/
post_views_count:
  - 167

---
会社で、VSSサーバの調子が悪くなった際に、バージョン管理なしは怖いと思って、TortoiseHGを入れました。

TortoiseHGについては、下記が役に立ちます。  
http://d.hatena.ne.jp/Wacky/20080503/1209817242  
http://sinproject.blog47.fc2.com/?q=tortoiseHG

しかし、問題点が2点ほど。  
・管理対象にできないファイルがある  
　おそらく何か処理できない日本語があると思われます。  
　まだパターンを見いだせていないですけど。  
・管理対象となっているフォルダの参照が遅い  
　最初の一発目だけかもしれませんが、エクスプローラが固まります。

ということで、本格利用はまだなのかな・・・  
まだ使いこなせていませんが、パッチをメールで送るようなことができそうなので、それができると、VSSを公開できない協力会社とも、ソース管理を一元化できてよいのですが。

おまけの一言  
たまに、VSSでチェックインしていない状態で、ソース管理側の状態を上書きしてしまい、「うおー、昨日の作業が消えた〜」とかやっちゃう人いますよね。  
それが怖いのもあって、私は最新版の取得は、バッチファイルを作って、現状のファイルのコピーをした上で最新を取得するようにしていたのですが、そのかわりと言う意味での二重バージョン管理は悪くないかなと思いますよ。  
上記のような状態なので、まだ本格的におすすめはしていませんけど。

<a href="http://px.a8.net/svt/ejp?a8mat=1HW73G+BB99U+348+15VMOX" target="_blank"><img height="60" border="0" width="468" alt="" src="http://www27.a8.net/svt/bgt?aid=090521836019&wid=001&eno=01&mid=s00000000404007034000&mc=1" /></a><img height="1" border="0" width="1" alt="" src="https://i1.wp.com/www13.a8.net/0.gif?resize=1%2C1" data-recalc-dims="1" /> 

<p style="color:#008;text-align:right;">
  <small><em>Powered by</em> <a href="http://www.qumana.com/">Qumana</a></small>
</p>