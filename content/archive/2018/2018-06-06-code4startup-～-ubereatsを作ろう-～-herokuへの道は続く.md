---
title: Code4StartUp ～ UberEatsを作ろう ～ herokuへの道は続く
author: KONNO Kiyotaka
type: post
date: 2018-06-06T13:57:30+00:00
archives:
    - 2018
url: /code4startup-～-ubereatsを作ろう-～-herokuへの道は続く/
post_views_count:
  - 1067
categories:
  - プログラミング
tags:
  - Code4Startup

---
<a href="https://code4startup.com/?ref=kiyotakakonno" target="_blank">Code4Startup</a>

前回からの続き

インストールされたということで、heroku loginしてみると、  
Error: login is not a heroku command.  
再インストールしなさいという情報があるので、  
curl https://cli-assets.heroku.com/install-ubuntu.sh | sh  
しかし、エラー変わらず。  
手当たり次第という感じですが、  
wget -qO- https://toolbelt.heroku.com/install-ubuntu.sh | sh  
変わらない。

<a href="https://teratail.com/questions/125977" target="_blank">https://teratail.com/questions/125977</a>  
に従ってみる。  
npm uninstall -g heroku  
これでもheroku &#8211;versionは出てくるが・・・  
wget https://cli-assets.heroku.com/heroku-cli/channels/stable/heroku-cli-linux-x64.tar.gz -O heroku.tar.gz  
tar -xvzf heroku.tar.gz  
mkdir -p /usr/local/lib /usr/local/bin  
sudo mv heroku-cli-v6.16.18-62346b1-linux-x64/ /usr/local/lib/heroku  
↓実際に作成されたディレクトリ名に変更  
sudo mv heroku-cli-v6.99.0-ec9edad-linux-x64/ /usr/local/lib/heroku  
sudo ln -s /usr/local/lib/heroku/bin/heroku /usr/local/bin/heroku  
失敗  
ln: failed to create symbolic link &#8216;/usr/local/bin/heroku&#8217;: File exists  
↓  
sudo unlink /usr/local/bin/heroku  
sudo ln -s /usr/local/lib/heroku/bin/heroku /usr/local/bin/heroku  
これで動くようになった

heroku &#8211;version  
▸ Cannot read property &#8216;concat&#8217; of undefined  
▸ Cannot read property &#8216;concat&#8217; of undefined  
heroku-cli/6.99.0-ec9edad (linux-x64) node-v9.11.1  
ちょっとメッセージが気になるけど・・・  
heroku loginも動作した。

<a href="https://code4startup.com/?ref=kiyotakakonno" target="_blank">Code4Startup</a>

<div class="kaerebalink-box">
  <div class="kaerebalink-image">
    <a href="https://www.amazon.co.jp/exec/obidos/ASIN/4873117585/jqinglong-22/" target="_blank"><img style="border: currentcolor; border-image: none;" src="https://i1.wp.com/images-fe.ssl-images-amazon.com/images/I/512ru2i5gyL._SL160_.jpg?ssl=1" data-recalc-dims="1" /></a>
  </div>
  
  <div class="kaerebalink-info">
    <div class="kaerebalink-name">
      <a href="https://www.amazon.co.jp/exec/obidos/ASIN/4873117585/jqinglong-22/" target="_blank">ゼロから作るDeep Learning ―Pythonで学ぶディープラーニングの理論と実装</a>
    </div>
    <div class="kaerebalink-powered-date">
      posted with <a href="https://kaereba.com" target="_blank" rel="nofollow">カエレバ</a>
    </div>
    <div class="kaerebalink-detail">
      斎藤 康毅 オライリージャパン 2016-09-24
    </div>
    <div class="kaerebalink-rank">
      <div class="kaerebalink-salesranking" style="margin-bottom: 5px;">
        売り上げランキング : 221
      </div>
    </div>
  </div>
  
  <div class="kaerebalink-footer">
  </div>
  
  <div class="kaerebalink-footer" style="clear: left;">
  </div>
</div>