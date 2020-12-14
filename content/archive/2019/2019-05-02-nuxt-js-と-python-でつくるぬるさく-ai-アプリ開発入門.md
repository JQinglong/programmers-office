---
title: Nuxt.js と Python でつくるぬるさく AI アプリ開発入門
author: KONNO Kiyotaka
type: post
date: 2019-05-02T06:49:11+00:00
archives:
    - 2019
url: /nuxt-js-と-python-でつくるぬるさく-ai-アプリ開発入門/
featured_image: /wp-content/uploads/2019/05/nullsuck.png
post_views_count:
  - 1312
categories:
  - プログラミング
tags:
  - AI
  - Docker
  - Nuxt.js
  - Python
  - Vue

---
技術書典6で購入した本2冊目。  
これも素晴らしい。<figure class="wp-block-embed-twitter wp-block-embed is-type-rich is-provider-twitter">

<div class="wp-block-embed__wrapper">
  <blockquote class="twitter-tweet" data-width="500" data-dnt="true">
    <p lang="ja" dir="ltr">
      <a href="https://twitter.com/hashtag/%E6%8A%80%E8%A1%93%E6%9B%B8%E5%85%B86?src=hash&ref_src=twsrc%5Etfw">#技術書典6</a> の <a href="https://twitter.com/hashtag/%E3%81%AC%E3%82%8B%E3%81%95%E3%81%8FAI?src=hash&ref_src=twsrc%5Etfw">#ぬるさくAI</a> ですが 14時に完売しました！！<br />ご購入いただいた皆様、本当にありがとうございました！！！<br /><br />BOOTHでのpdf販売を同時に開始しましたので<br />ぜひ、<a href="https://twitter.com/hashtag/%E6%8A%80%E8%A1%93%E6%9B%B8%E5%85%B8?src=hash&ref_src=twsrc%5Etfw">#技術書典</a> にお越しいただけなかった方、ご購入ください！<a href="https://t.co/S7fajL0B8o">https://t.co/S7fajL0B8o</a>
    </p>&mdash; takayama.k (@pco2699) 
    <a href="https://twitter.com/pco2699/status/1117323207537598464?ref_src=twsrc%5Etfw">April 14, 2019</a>
  </blockquote>
</div></figure> 

なんとか連休中に平成最初のリリースまで持って行きたかったのですが、色々つまり出してきたので、実際に何かを作ってリリースするところを目指したいと思い、Docker環境構築までで一旦まとめておきたいと思います。

## Jupyter Notebook

いきなり、あなたの知らない世界で、Jupyter Notebook のインストールから。  
こちらなども参考に。  
<https://techacademy.jp/magazine/17430>

まずはAnaconda をインストール。Anaconddaで2.3GBも使うんですね・・・

インストールしたら、  
Enviroments > 「analytics」  
Notebookをインストールしようとして間違えてJupyterLabをインストールしてしまいました。そうしたらNotebookも勝手に入りました。

## 3.3.1 データセットを読み込む

第１章、第２章も読み応えありますが、作り始めるのは第３章からになります。

初めてJupyter Notebook を使う身としては、色々不明点を抱えながら進めます。どうやって実行するんだ、というところから始まりますが、Runボタンで実行です。

実行すると、エラー。

<pre class="wp-block-code"><code>ModuleNotFoundError                       Traceback (most recent call last)
&lt;ipython-input-2-aed2979e33dd> in &lt;module>
      1 # 分析に必要なライブラリをインポート
----> 2 import pandas as pd
      3 import numpy as np
      4 
      5 # データセットを読み込む

ModuleNotFoundError: No module named 'pandas'</code></pre>

先に  
5.5.1 機械学習に必要なライブラリをインストールする  
を実行します。  
pipenv install scikit-learn pandas numpy

そうすると、さらにその前に、  
5.3.1 pipenv のインストール  
pip install pipenv  
が必要となります。

## 3.6.2 データ分割

いきなり実行すると

<pre class="wp-block-code"><code>NameError                                 Traceback (most recent call last)
&lt;ipython-input-17-6ab9212361b9> in &lt;module>
      1 # 目的変数
----> 2 Y = df2["delicious"]
      3 # 説明変数
      4 X = df2.drop(["quality", "delicious"], axis=1)
      5 

NameError: name 'df2' is not defined</code></pre>

となってしまいます。直前の実行結果は引き継がれるようですので、先に、df2 = df としておくと大丈夫のようです。

## **3.6.3** 機械学習 

こちらも

<pre class="wp-block-code"><code>ModuleNotFoundError                       Traceback (most recent call last)
&lt;ipython-input-18-ad2ebbb1e040> in &lt;module>
      9 from sklearn.linear_model import LogisticRegression
     10 # 交差検証
---> 11 from sklearn.cross_validation import train_test_split
     12 # インスタンス作成
     13 log_model = LogisticRegression()

ModuleNotFoundError: No module named 'sklearn.cross_validation'</code></pre>

<https://www.haya-programming.com/entry/2018/12/04/052713>  
を参考にして、  
sklearn.cross_validation  
↓  
sklearn.model_selection  
に変更します。

## 4.3.2 プロジェクト作成

<pre class="wp-block-code"><code>-bash: npx: command not found</code></pre>

こんなのが一々エラーになってしまうので、最初に環境を殿と得るべきだし、最後にDocker環境でどの環境を使うかでまた問題になるので、最初から環境はDockerでバージョンを固定して作るのが良いのでしょうね。  
とりあえず、続けました。インストールは下記を参照します。  
<a href="https://www.suzu6.net/posts/45/" target="_blank" rel="noreferrer noopener" aria-label="https://www.suzu6.net/posts/45/ (opens in a new tab)">https://www.suzu6.net/posts/45/</a>

さて、書籍ではNullSuckディレクトリに、Project name はNullSuckで作ることになっています。  
4.1.1 全体のプロジェクト構成　に記載の「NullSuck-AI」と一致していないので、最初は、 NullSuck-AIディレクトリにNullSuckプロジェクトを作ってみました。  
すると、まず、Warning: name can no longer contain capital letters　が出ている。  
さらに、下記エラーが出ています。

<pre class="wp-block-code"><code>Installing packages with yarnTrace: Error: spawn yarn ENOENT
     at Process.ChildProcess._handle.onexit (internal/child_process.js:248:19)
     at onErrorNT (internal/child_process.js:431:16)
     at processTicksAndRejections (internal/process/task_queues.js:84:17) {
   errno: 'ENOENT',
   code: 'ENOENT',
   syscall: 'spawn yarn',
   path: 'yarn',
   spawnargs: [ 'install' ]
 }
</code></pre>

この時点で作成された構成も4.1.1 全体のプロジェクト構成のものとは全く異なります。  
正解は、4.3.5 プロジェクト構成。  
なので、正解は、NullSuck-AI/client に、プロジェクトnullsuckを作るという感じになります。

さらに、最後に選択する、Choose a package manager　をyarnではなくnpmにしてはどうか。  
（yarnインストールしていないし）  
これでとりあえずはできました。

## 4.3.3 プロジェクトの TypeScript 対応を行う

これについては、具体的な記述は書いてくれていないので、githubのソースを参考に書き換えようと思ったが、若干内容が異なっているのでそのままにしておく。まずは起動してみよう。

起動も、yarn run dev　ではなくnpm run dev。  
ここで、yarnを入れておくべきだったと気づく（結局、後で入れることになりますが）が、とりあえず起動させよう。OK！

と思ったが、Insert `·` prettier/prettier　のようなエラー多数。  
これの解消は、

<pre class="wp-block-code"><code>node_modules/.bin/eslint --fix --ext .js,.vue --ignore-path .gitignore .</code></pre>

## 4.5.1 診断項目カードを作ろう

とりあえず進んでいきます。  
FormCard.vue の置き場は、componentsの下ではなく、components/Form。（後で変更しますが）

## 4.5.2 診断カードをたくさん出せるようにしよう

<pre class="wp-block-code"><code>error  Parsing error: Using the export keyword between a decorator and a class is not allowed. Please use `export @dec class` instead.</code></pre>

ここに至って、4.3.3 プロジェクトの TypeScript 対応を行うに戻って、TypeScript 対応を行うことにします。

ただし、現在の環境は、2.6.3（書籍は、2.4.0 ）。  
そもそも、nuxt 本体で TypeScript をサポートしてくれるので nuxt-ts はもう不要になったようです。  
<a rel="noreferrer noopener" aria-label="https://qiita.com/shts/items/e7da59cc568a98d55fb5 (opens in a new tab)" href="https://qiita.com/shts/items/e7da59cc568a98d55fb5" target="_blank">https://qiita.com/shts/items/e7da59cc568a98d55fb5</a>

このタイミングで、ついでにyarnもインストールします。

<pre class="wp-block-code"><code>ERROR  Cannot import module 'ts-node'</code></pre>

これに対応するためには、

<pre class="wp-block-code"><code>yarn add ts-node -D</code></pre>

<pre class="wp-block-code"><code>&lt;form-card v-for="i in 11" :key="‘${i}‘"/></code></pre>

はダメと言われるので、いったん

<pre class="wp-block-code"><code>&lt;form-card v-for="i in 11" :key="i" /></code></pre>

にするとOKとか。

しかし、その後もあれこれ、エラーと戦いますが、なかなか動いてくれない。

ここで、一旦リセット。  
まずは、これに従います。  
TypeScript Support &#8211; Nuxt.js  
<a href="https://nuxtjs.org/guide/typescript/" target="_blank" rel="noreferrer noopener" aria-label="https://nuxtjs.org/guide/typescript/ (opens in a new tab)">https://nuxtjs.org/guide/typescript/</a>

ここで、&#8211;fix は、yarn lint &#8211;fix　で良いのだと知ったり。

それでもまだ。

<pre class="wp-block-code"><code>Cannot find module 'nuxt-class-component'.</code></pre>

に対しては、

<pre class="wp-block-code"><code>yarn add nuxt-class-component</code></pre>

とか。  
もう一息というところに立ちはだかるのは、

<pre class="wp-block-code"><code>Cannot set property 'components' of undefined</code></pre>

というエラーでした。最初は、このメッセージで検索したりしていたのですが、冷静になって考えると、問題は、componentsにあるのではなく、それが属するものが、取得できていないということで、undefinedになってしまっているわけです。要は、JSにおける、ヌルポです。  
FormCardがオブジェクトとして認識できていないということであり、すなわちちゃんとインポートされていないということなので、そこを見直すべきという結論にやっとたどり着きました。ここは結構長かった。

結論としては、4.5.1 診断項目カードを作ろうの、FormCard.vueの記述は、下記のようにします。

<pre class="wp-block-code"><code>&lt;script lang="ts">
import { Component, Vue } from 'vue-property-decorator'
  @Component
export default class FormCard extends Vue {}
&lt;/script></code></pre>

すなわち、@Component　を付けます。ここでやっと画面が開きました。

## **4.6** ヌルサクグラフを実装しよう 

今度は、グラフ表示用のコンポーネントを作って、読み込もうということですが・・・

<pre class="wp-block-code"><code>30:28 Property 'wineAttributes' has no initializer and is not definitely assigned in the constructor.
    29 |   @Mutation('SET_TITLE') setTitle
  > 30 |   @Getter('GET_WINE_ATTR') wineAttributes: WineAttribute[]
       |                            ^
    31 |   @Getter('IS_ALL_VALUE_SETTED') isAllValueSetted</code></pre>

コンストラクタで初期化しましょう、の意味。・・・どこで？？

一旦強引に

<pre class="wp-block-code"><code>  GET_WINE_ATTR: (state: State): WineAttribute[] => {
    let wAttr: WineAttribute[] = []
    if (state.wineAttributes.length > 0) {
      wAttr = state.wineAttributes
    }
    return wAttr
  },</code></pre>

みたいなことをやってみると、そこは進んで、is not in camel case　エラーになったので、言われるがままにcamel caseに直します。しかし、そうすると、また、no initializer　エラー。結局対処がわからず、tsconfig.json　に

<pre class="wp-block-code"><code>"strictPropertyInitialization": false</code></pre>

を追記しました。

これでサーバは起動するようになりましたが、ページを開こうとすると、

<pre class="wp-block-code"><code>FATAL ERROR: Ineffective mark-compacts near heap limit Allocation failed - JavaScript heap out of memory</code></pre>

ギブアップ。先に進むことにします。

## 5.3.2 pipenv でプロジェクトを作ろう

書籍では、

<pre class="wp-block-code"><code>mkdir responder_test && cd responder_test</code></pre>

と書いていますが、そのフォルダにPipfileが作成されるようなので、serverフォルダでpipenv installを実行すれば良いものと考えられます。

## 5.4.2 ハンドラを実装しよう

これは、handlers.py　についての記述です。

## 5.5.1 機械学習に必要なライブラリをインストールする

3.3.1で実行してあったわけですが、念の為もう一度実行しておく  
インストールは動きますが、すぐに完了します。

## 5.5.2 モデルを読み込む Service を作成する

書籍ではservice.py、githubではservices.py。  
正解は、5.2 プロジェクトの構成 でもservices.pyになっているので、それに従います。

## 6.2.1 Dockerfile の作成

基本的には、githubのDockerfileをもらってきて、バージョンはローカルの環境に合わせる。

## これ以降について

バージョン関係については、現場でこうなったら収集つかないなということで、今後はやはりコンテナを活用して、開発からリリースまでをキレにつなげていくことが求められるということでしょうね。オープンソースを活用した開発というものはそういうものだ。けど、それとは違う世界もまだまだあるというのも実感。

で、このまま頑張っても簡単なサンプルが動くようになって、今度はGoogleから請求が来たりするのだろうと思われるので、一旦終了。

そして自分のデータで動かすものを作りたいですが、どうしようかな・・・連休中に何か動かしたいですがね。

<div class="kaerebalink-box" style="text-align:left;padding-bottom:20px;font-size:small;zoom: 1;overflow: hidden;">
  <div class="kaerebalink-image" style="float:left;margin:0 15px 10px 0;">
    <a href="//af.moshimo.com/af/c/click?a_id=1238335&#038;p_id=54&#038;pc_id=54&#038;pl_id=616&#038;s_v=b5Rz2P0601xu&#038;url=https%3A%2F%2Fproduct.rakuten.co.jp%2Fproduct%2F-%2Fd879ed0dc255fa54dc9757face4232ec%2F" target="_blank"  rel="noopener noreferrer"><img src="https://i1.wp.com/thumbnail.image.rakuten.co.jp/ran/img/2001/0009/784/863/542/563/20010009784863542563_1.jpg?ssl=1" style="border: none;" data-recalc-dims="1" /></a><img src="//i.moshimo.com/af/i/impression?a_id=1238335&#038;p_id=54&#038;pc_id=54&#038;pl_id=616" width="1" height="1" style="border:none;" />
  </div>
  
  <div class="kaerebalink-info" style="line-height:120%;zoom: 1;overflow: hidden;">
    <div class="kaerebalink-name" style="margin-bottom:10px;line-height:120%">
      <a href="//af.moshimo.com/af/c/click?a_id=1238335&#038;p_id=54&#038;pc_id=54&#038;pl_id=616&#038;s_v=b5Rz2P0601xu&#038;url=https%3A%2F%2Fproduct.rakuten.co.jp%2Fproduct%2F-%2Fd879ed0dc255fa54dc9757face4232ec%2F" target="_blank"  rel="noopener noreferrer">Ｎｕｘｔ．ｊｓビギナーズガイド Ｖｕｅ．ｊｓベースのフレームワークによるシングルペ /シ-アンドア-ル研究所/花谷拓磨</a><img src="//i.moshimo.com/af/i/impression?a_id=1238335&#038;p_id=54&#038;pc_id=54&#038;pl_id=616" width="1" height="1" style="border:none;" />
      <div class="kaerebalink-powered-date" style="font-size:8pt;margin-top:5px;font-family:verdana;line-height:120%">
        posted with <a href="https://kaereba.com" rel="nofollow noopener noreferrer" target="_blank">カエレバ</a>
      </div>
    </div>
    <div class="kaerebalink-detail" style="margin-bottom:5px;">
    </div>
    <div class="kaerebalink-link1" style="margin-top:10px;">
    </div>
  </div>
  
  <div class="booklink-footer" style="clear: left">
  </div>
</div>