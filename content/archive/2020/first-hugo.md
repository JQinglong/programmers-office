---
title: "初めての Hugo"
author: KONNO Kiyotaka
date: 2020-12-11T23:27:56+09:00
archives:
    - 2020
categories:
  - プログラミング
draft: false
---
## 経緯
これまで、あちこちで駄文を積み重ねてきました。

最初は、ソネットで、無料ホームページを作成し、1999年当時はブログというものはなかったため、日記的なメモを書いていました。
これは、現在は、xdomainに置いています。
いまだに参照できるのはありがたいことです。  
[select *](http://jqinglong.html.xdomain.jp/konnokiyotaka/)  

2003年12月、Niftyと契約したこともあり、ココログでブログを始めました。
その後、契約をやめる2014年まで継続したものを、ブログ契約だけは継続し、情報を残しています。  
[一プログラマのラグジュアリーな生活Ⅱ](http://pgblog-japan.cocolog-nifty.com/blog/2003/12/index.html)  

ココログは残したものの、WordPressを使ってみたいという欲求が出てきたことで、新たにブログを立ち上げました。  
[一プログラマのチャイニーズな生活](http://jqinglong.wp.xdomain.jp/)  
データは引き継いでいるので、2003年情報から残っており、2018年12月まで書いていました。

今度は、サイトをSSL化したいという欲求と、合わせて、たまたまだったと思いますが、GCPの無料枠でWordPress環境を構築できるという情報を見て、GCPへの移行を行いました。  
[Programmers Office](https://www.programmers-office.ml/)

これが直近のサイトですが、GCPの無料枠では若干遅さを感じるのと、原因はわかっていませんが、何度やっても Google
 AdSense 申請が通らない（前のサイトでは通っているので内容ではないと思われるが、その後の記事に問題があるのか）。
 そしてこれが決定打ですが、無料ドメインサービス freenom の 無料での更新ができない（本来、無料枠での１年以内での更新期間の選択肢が出てくるはずなのですが、有料枠のの１年以上の更新しか出てきません。これも原因不明）。
ということでさらに別の移行を検討してみたところ、WordPressからの移行記事を見たということで、Hugoを試してみようか、ということにしました。

## 謝辞
以下のサイトに大変お世話になりました。

[HUGOのテーマ「Mainroad」の設定方法を紹介](https://itsys-tech.com/list/hugo/007/)

[Hugo によるブログ作成と mainroad テーマのカスタマイズ](https://terashim.com/posts/create-hugo-blog-and-customize-mainroad-theme/)

[GitHub Actions による GitHub Pages への自動デプロイ](https://qiita.com/peaceiris/items/d401f2e5724fdcb0759d)
