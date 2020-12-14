---
title: TruffleBoxs 入門
author: KONNO Kiyotaka
type: post
date: 2020-03-23T07:52:01+00:00
archives:
    - 2020
url: /truffleboxs-入門/
featured_image: /wp-content/uploads/2018/11/imac-300x300.jpg
post_views_count:
  - 232
categories:
  - プログラミング
tags:
  - ブロックチェーン

---
改めて勉強しようと考えたときに、TruffleBoxs が良いのではと思い立ちました。

まずは、純粋に  
TruffleBox (React&Truffle)を用いたDockerでのdapps（ブロックチェーンアプリ）の開発環境の構築  
<a href="https://qiita.com/dl10yr/items/26b106d27a2de87da131" target="_blank" rel="noreferrer noopener" aria-label="https://qiita.com/dl10yr/items/26b106d27a2de87da131 (opens in a new tab)">https://qiita.com/dl10yr/items/26b106d27a2de87da131</a>  
こちらをなぞらせていただきます。

いきなり、DockerFile の配置場所の絵と、docker-compose.yml の記述が食い違い？？  
docker-compose.yml の記述に合わせて、truffle フォルダに配置します。  
Dockerfile のfは小文字で

<pre class="wp-block-code"><code>$ docker-compose build
$ docker-compose run truffle truffle unbox react</code></pre>

Docker 側からアクセスできるように、Ipアドレスを追加するところ。  
まずは、事前確認。

<pre class="wp-block-code"><code>ifconfig
 lo0: flags=8049 mtu 16384
         options=1203
         inet 127.0.0.1 netmask 0xff000000 
         inet6 ::1 prefixlen 128 
         inet6 fe80::1%lo0 prefixlen 64 scopeid 0x1 
         nd6 options=201
 ・・・</code></pre>

変更

<pre class="wp-block-code"><code>sudo ifconfig lo0 alias 10.200.10.1/24</code></pre>

事後確認

<pre class="wp-block-code"><code>ifconfig
 lo0: flags=8049 mtu 16384
         options=1203
         inet 127.0.0.1 netmask 0xff000000 
         inet6 ::1 prefixlen 128 
         inet6 fe80::1%lo0 prefixlen 64 scopeid 0x1 
         inet 10.200.10.1 netmask 0xffffff00 
         nd6 options=201
 ・・・</code></pre>

これに基づいて、truffle-config.jsの設定。  
作成された状態での初期値では、port: 8545 で作られるが、ganacheが7545なので、7545に変更してみました。  
ネットワークの名前は、developmentではなく、初期値のdevelopのままにしておきます。  
すると、色々問題がありました。

<pre class="wp-block-code"><code>$ docker-compose run truffle truffle migrate
$ docker-compose up</code></pre>

この状態で、ブラウザで  
http://localhost:8003/  
を叩くことにより、接続確認の狐が出てきて、画面は起動しますが、すぐエラー画面に遷移します。

<pre class="wp-block-code"><code>Unhandled Rejection (Error): This contract object doesn't have address set yet, please set an address first.
▶ 2 stack frames were collapsed.
App.runExample
src/app/client/src/App.js:42
  39 | const { accounts, contract } = this.state;
  40 | 
  41 | // Stores a given value, 5 by default.
> 42 | await contract.methods.set(5).send({ from: accounts&#91;0] });
     | ^  43 | 
  44 | // Get the value from the contract to prove it worked.
  45 | const response = await contract.methods.get().call();
View compiled
▶ 22 stack frames were collapsed.
App.componentDidMount
src/app/client/src/App.js:28
  25 | 
  26 |   // Set web3, accounts, and contract to the state, and then proceed with an
  27 |   // example of interacting with the contract's methods.
> 28 |   this.setState({ web3, accounts, contract: instance }, this.runExample);
     | ^  29 | } catch (error) {
  30 |   // Catch any errors for any of the above operations.
  31 |   alert(
View compiled</code></pre>

これは、ganacheのアドレスを変えた後に、保存していないだけでした。たいへんすみません。  
しかし保存してみても、

<pre class="wp-block-code"><code>Failed to load web3, accounts, or contract. Check console for details.</code></pre>

というメッセージで、

<pre class="wp-block-code"><code>Loading Web3, accounts, and contract…</code></pre>

という画面

もういちどDocker を終了して、

<pre class="wp-block-code"><code>docker-compose run truffle truffle migrate</code></pre>

すると、

<pre class="wp-block-code"><code> Could not connect to your Ethereum client with the following parameters:
     - host       > 127.0.0.1
     - port       > 7545
     - network_id > 5777</code></pre>

というエラーになっていた。  
ちなみに、

<pre class="wp-block-code"><code>cd truffle
truffle console</code></pre>

してみると

<pre class="wp-block-code"><code>No network available. Use truffle develop or add network to truffle.js config.</code></pre>

そんなことをしているとだんだん分かってきました。  
truffle-config.js はやはり、development にしないとそのままでは認識されません。  
合わせて、ポートも8545に変更。

また、metamaskの設定も  
http://10.200.10.1:8545  
と、アドレスを変更する必要があります。

というわけで無事表示されました。表示されたけど残高不足！  
まあ、そんな感じですね。<figure class="wp-block-image size-large">

<img src="https://i0.wp.com/www.programmers-office.ml/wp-content/uploads/2020/03/スクリーンショット-2020-03-23-16.28.17.png?ssl=1" alt="" class="wp-image-3263" srcset="https://i0.wp.com/www.programmers-office.ml/wp-content/uploads/2020/03/スクリーンショット-2020-03-23-16.28.17.png?w=320&ssl=1 320w, https://i0.wp.com/www.programmers-office.ml/wp-content/uploads/2020/03/スクリーンショット-2020-03-23-16.28.17.png?resize=194%2C300&ssl=1 194w" sizes="(max-width: 320px) 100vw, 320px" data-recalc-dims="1" /> </figure>