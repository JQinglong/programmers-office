---
title: Code4StartUp ～ UberEatsを作ろう ～ herokuへの道
author: KONNO Kiyotaka
type: post
date: 2018-06-01T13:13:48+00:00
archives:
    - 2018
url: /code4startup-～-ubereatsを作ろう-～-herokuへの道/
post_views_count:
  - 1112
categories:
  - プログラミング
tags:
  - Code4Startup

---
<a href="https://code4startup.com/?ref=kiyotakakonno" target="_blank">Code4Startup</a>

講義ビデオは突然heroku loginから始まった。  
しかし、cloud9ではherokuコマンドは効かない。  
よって、インストールから。

<a href="http://www.lib-arc.com/entry/2018/04/15/234355" target="_blank">http://www.lib-arc.com/entry/2018/04/15/234355</a>  
こちらでは、nodeは入っている前提。しかし、少なくとも私の環境には入っていない。  
そこから。となると、こちらを参考。  
<a href="https://qiita.com/beplocks661/items/8d840b6efcdcd14009bf" target="_blank">https://qiita.com/beplocks661/items/8d840b6efcdcd14009bf</a>  
と思ったらnvm: command not found。  
<a href="https://qiita.com/seibe/items/36cef7df85fe2cefa3ea" target="_blank">https://qiita.com/seibe/items/36cef7df85fe2cefa3ea</a>  
ここから。  
sudo apt-get install -y nodejs npm  
sudo npm cache clean  
sudo npm install n -g  
sudo n stable  
node -v  
　v10.2.1

ここからやっとherokuインストール  
npm install -g heroku-cli  
インストールは始まったけど、エラー  
・・・  
npm ERR! Please try running this command again as root/Administrator.  
・・・  
sudo npm install -g heroku-cli  
でOK  
heroku -v  
　heroku-cli/7.0.9 linux-x64 node-v10.2.1  
という感じでよいのでしょうか。

開発環境構築の基礎を学べます。  
ん？cloud9って、こういうものでしたっけ？？

<a href="https://code4startup.com/?ref=kiyotakakonno" target="_blank">Code4Startup</a>

<a href="https://px.a8.net/svt/ejp?a8mat=2ZIWSJ+4J4U2Q+UBO+U3W29" target="_blank" rel="nofollow"><br /> <img width="300" height="250" alt="" src="https://www21.a8.net/svt/bgt?aid=180601219274&wid=003&eno=01&mid=s00000003930005057000&mc=1" border="0" /></a>  
<img width="1" height="1" alt="" src="https://i0.wp.com/www18.a8.net/0.gif?resize=1%2C1&#038;ssl=1" border="0" data-recalc-dims="1" />