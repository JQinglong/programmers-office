---
title: MacにDocker環境をビジュアルに構築する
author: KONNO Kiyotaka
type: post
date: 2019-01-05T22:17:45+00:00
url: /macにdocker環境をビジュアルに構築する/
featured_image: /wp-content/uploads/2018/11/imac-300x300.jpg
post_views_count:
  - 557
categories:
  - プログラミング
tags:
  - Docker
  - Magento

---
## 目的

2018年11月にMagentoが2.3にバージョンアップしたため、その環境を作りたい。  
しかし、現在AWSに構築している環境をバージョンアップするのは、素人には難しそう。そもそも、現状が綺麗にできていない気がするので、クリーンインストールすることにする。  
そして、今後も複数バージョンをどう取り扱うか問題は出てくると思うので、このWordpressサイト構築にあたって興味を持ったDockerをもう少し突き詰めてみる。

## 考えること

Dockerもコマンド打つだけじゃないでしょ、もっとビジュアルに行こうぜ！と思ったら、思いの外深い。  
参考  
<a rel="noreferrer noopener" target="_blank" href="https://yoshinorin.net/2017/08/30/try-docker-rancher/">https://yoshinorin.net/2017/08/30/try-docker-rancher/</a>

まず、Docker for Macにするのか、Docker Toolboxにするのかを考えなければなりません。  
一般的には、VirtualBoxが不要であるDocker for Macの方が、早い、ということのようです。  
そして、実際のビジュアルツールとして、やはり本命はDocker社純正のKitematicと言うことになるかと思います。  
ただ、上記参考サイトにあるように、これは「Docker for WindowsとDocker for Mac」用となるので、AWS等のLinux環境では同一環境にはならないと言うことになります。  
もっとも、それは「外側」が異なるという話であり、Dockerで構築される「中身」については同じでしょうから、それは別の話として良いのかなと考え、Kitematicで構築することにしてみます。  
なお、第二の選択肢として、Portainer、Rancherも興味深いです。

## Kitematicのインストール

  
手順としては、Docker for Macをインストールし、そうすると、Dockerアイコンが表示されるようになるので、そこからKitematicをインストールするということのようです。  
この辺が比較的新し目の情報かと思います。  
<a rel="noreferrer noopener" target="_blank" href="https://yatteq.com/localdev-docker">https://yatteq.com/localdev-docker</a>  
で、Docker for Macをダウンロードしに行くわけですが、そこの名前はDocker Desktop (Mac)。分かりにくくないですか？？  
Dockerのアカウント登録をして、ダウンロードします。518MB、なかなかですね・・・  
インストール方法は特筆すべきことはないですが、本家docsでも眺めておけば良いでしょう。  
<a rel="noreferrer noopener" target="_blank" href="https://docs.docker.com/docker-for-mac/install/#install-and-run-docker-for-mac">https://docs.docker.com/docker-for-mac/install/#install-and-run-docker-for-mac</a>  
丁寧な手順はこちらとか。  
<a rel="noreferrer noopener" target="_blank" href="https://qiita.com/seijimomoto/items/357ac7aa84f98b96021f">https://qiita.com/seijimomoto/items/357ac7aa84f98b96021f</a>  
最初、Docker アイコンからKitematicをクリックしても反応なく焦りましたが、再度アプリケーションフォルダからDockerをダブルクリックしたら反応してくれました。  
ということで、インストールまでは、簡単に行きます。

<a href="//af.moshimo.com/af/c/click?a_id=1261906&#038;p_id=936&#038;pc_id=1196&#038;pl_id=14103&#038;guid=ON" target="_blank" rel="nofollow"><img src="https://i2.wp.com/image.moshimo.com/af-img/0288/000000014103.png?resize=468%2C60" width="468" height="60" style="border:none;" data-recalc-dims="1" /></a><img src="//i.moshimo.com/af/i/impression?a_id=1261906&#038;p_id=936&#038;pc_id=1196&#038;pl_id=14103" width="1" height="1" style="border:none;" />