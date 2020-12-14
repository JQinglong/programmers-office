---
title: 'Amazon アソシエイト Web サービス&rarr;「Product Advertising API」に変更'
type: post
date: 2009-05-24T13:30:00+00:00
archives:
    - 2009
url: /amazon-アソシエイト-web-サービス「product-advertising-api」に変更/
post_views_count:
  - 788

---
若干乗り遅れていますが、  
<a href="http://b-shopping.appspot.com/product/" target="_blank">B-Shopping</a>も<a href="http://affibook.appspot.com/search/search" target="_blank">AffiBook!!</a>も対応しなければいけません。 

要は  
<http://docs.amazonwebservices.com/AWSECommerceService/latest/DG/index.html?rest-signature.html>  
をやれと言うことですね。 

<http://d.hatena.ne.jp/niiyan/20090509/1241884365>  
を参考にやってみました。 

リクエスト先も  
http://ecs.amazonaws.jp  
から  
http://webservices.amazon.co.jp  
に変わっているんですかね。 

クエリの組み立ては、下記のようにしていたので、単純にそれで作られるListの  
sort()でやりました。  
&nbsp;&nbsp; query = [  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; (&#8216;Service&#8217;, service),  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; (&#8216;AWSAccessKeyId&#8217;, accessKeyId),  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; (&#8216;Operation&#8217;, operation),  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; (&#8216;SearchIndex&#8217;, searchIndex),  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; (&#8216;ResponseGroup&#8217;, responseGroup),  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; (&#8216;Keywords&#8217;, self.params.get(&#8216;Keywords&#8217;, None).encode(&#8216;utf-8&#8217;)),  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; (&#8216;AssociateTag&#8217;, associateTag),  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; (&#8216;Version&#8217;, version),  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; (&#8216;Timestamp&#8217;, timestamp),  
&nbsp;&nbsp; ]  
&nbsp;&nbsp; query.sort() 

とりあえず返ってきているので、良しなのでしょうか（ちなみに、このsort()を  
しないと返ってこないので、効いているようです）。

<a href="http://www.accesstrade.net/at/c.html?rk=01000a410044mz" target="_blank"><img border="0" alt="" src="http://www.accesstrade.net/at/r.html?rk=01000a410044mz" /></a>