---
title: Docker push AWS ECR 編
author: KONNO Kiyotaka
type: post
date: 2019-01-19T05:33:30+00:00
url: /docker-push-aws-ecr-編/
featured_image: /wp-content/uploads/2019/01/スクリーンショット-2019-01-14-19.23.43.jpg
post_views_count:
  - 697
categories:
  - プログラミング
tags:
  - AWS
  - Docker

---
色々な編ができていく・・・

ずっとはまっていてもダメなので、ちょっとGitLabからのPullはどこかで質問することにします。  
そして、AWS ECS で pull するのであれば、当然相性良いだろうと思われる、ECR にpushしてみます。  
_イメージのプッシュ_  
<a rel="noreferrer noopener" target="_blank" href="https://docs.aws.amazon.com/ja_jp/AmazonECR/latest/userguide/docker-push-ecr-image.html">https://docs.aws.amazon.com/ja_jp/AmazonECR/latest/userguide/docker-push-ecr-image.html</a>

もうpushするimageはできているところからスタートします。  
_Docker 環境をステージング環境へ（Docker push編）_  
<a rel="noreferrer noopener" target="_blank" href="https://www.programmers-office.ml/2019/01/14/docker-%E7%92%B0%E5%A2%83%E3%82%92%E3%82%B9%E3%83%86%E3%83%BC%E3%82%B8%E3%83%B3%E3%82%B0%E7%92%B0%E5%A2%83%E3%81%B8%EF%BC%88docker-push%E7%B7%A8%EF%BC%89/">https://www.programmers-office.ml/2019/01/14/docker-%E7%92%B0%E5%A2%83%E3%82%92%E3%82%B9%E3%83%86%E3%83%BC%E3%82%B8%E3%83%B3%E3%82%B0%E7%92%B0%E5%A2%83%E3%81%B8%EF%BC%88docker-push%E7%B7%A8%EF%BC%89/</a>

## python環境

pushするためには、まず1.の認証が必要です。  
そのために、AWS CLIのインストールが必要です。  
まあ、そうなんだろうけど面倒は面倒ですね。どんどん遡る・・・  
結局、開発環境をDockerで作るとしても、それを扱うための環境（ここで言えばpython環境）をローカルに作らなければいけない。もう少しローカル依存を減らしたいのですが・・・  
_AWS CLI をインストールする方法_  
<a rel="noreferrer noopener" target="_blank" href="https://docs.aws.amazon.com/ja_jp/cli/latest/userguide/cli-chap-install.html">https://docs.aws.amazon.com/ja_jp/cli/latest/userguide/cli-chap-install.html</a>  
おもむろに

<blockquote class="wp-block-quote">
  <p>
    $ pip install awscli &#8211;upgrade &#8211;user
  </p>
</blockquote>

を叩くと、「pip: command not found」のつれないメッセージ。

<blockquote class="wp-block-quote">
  <p>
    $ python -m pip -V<br />/usr/bin/python: No module named pip
  </p>
</blockquote>

そこからか・・・

### python3  


そもそも、macの初期インストールpythonは

<blockquote class="wp-block-quote">
  <p>
    python &#8211;version<br />Python 2.7.10
  </p>
</blockquote>

です。  
pipはPython 3.4以降には、標準で付属しているそうです。  
Python3系を入れましょう。  
Code4Startupの時は、普通にインストーラーをダウンロードする形でしたが、今時だとやはり、Homebrewでしょうか。  
<a rel="noreferrer noopener" target="_blank" href="https://brew.sh/index_ja.html">https://brew.sh/index_ja.html</a>  
インストールのスクリプトを素直に実行。  
インストール完了後、

<blockquote class="wp-block-quote">
  <p>
    $ brew doctor<br />Your system is ready to brew.<br />
  </p>
</blockquote>

珍しく、すんなりインストールされました。

次に、pythonをどのように入れるか、こちらが参考になります。  
_Python3インストール（Mac編）_  
<a rel="noreferrer noopener" target="_blank" href="https://qiita.com/ms-rock/items/72b8f1abc661c539bb09">https://qiita.com/ms-rock/items/72b8f1abc661c539bb09</a>  
いくつか方法がありますが、「2.3. Homebrew + pyenvでのインストール方法」に従います。  
現時点で最新は3.7.2ですので、

<blockquote class="wp-block-quote">
  <p>
    pyenv install 3.7.2<br />
  </p>
</blockquote>

を叩きますと、インストールされていきますが、最後  
zipimport.ZipImportError: can&#8217;t decompress data; zlib not available  
というエラーを吐いています。  
そこで、  
<a rel="noreferrer noopener" target="_blank" href="https://qiita.com/zreactor/items/c3fd04417e0d61af0afe">https://qiita.com/zreactor/items/c3fd04417e0d61af0afe</a>  
を参考に、

<blockquote class="wp-block-quote">
  <p>
    sudo installer -pkg /Library/Developer/CommandLineTools/Packages/macOS_SDK_headers_for_macOS_10.14.pkg -target /
  </p>
</blockquote>

そして、もう一度、pyenv install 3.7.2・・・OK。  
この時点では

<blockquote class="wp-block-quote">
  <p>
    $ python &#8211;version<br />Python 2.7.10
  </p>
</blockquote>

<blockquote class="wp-block-quote">
  <p>
    $ pyenv global 3.7.2<br />$ pyenv versions<br />* system (set by /Users/aaa/.pyenv/version)<br /> 3.7.2
  </p>
</blockquote>

良し！と思うも、

<blockquote class="wp-block-quote">
  <p>
    $ python &#8211;version<br />Python 2.7.10<br />
  </p>
</blockquote>

あれ。いったん、ターミナル終了して再度。  


<blockquote class="wp-block-quote">
  <p>
    $ python &#8211;version<br />Python 3.7.2<br />
  </p>
</blockquote>

・・・そういうもの？

## AWS CLI

pipも使えるようになったので、

<blockquote class="wp-block-quote">
  <p>
    pip install awscli &#8211;upgrade &#8211;user<br />
  </p>
</blockquote>

色々動いて、インストールされたようです。

さらに、  
_AWS CLI 実行ファイルをコマンドラインパスに追加する_  
<a rel="noreferrer noopener" target="_blank" href="https://docs.aws.amazon.com/ja_jp/cli/latest/userguide/install-macos.html#awscli-install-osx-path">https://docs.aws.amazon.com/ja_jp/cli/latest/userguide/install-macos.html#awscli-install-osx-path</a>  
では、パスの確認方法が書いてありますが、それでは確認できず、

<blockquote class="wp-block-quote">
  <p>
    $ pip show awscli<br />/Users/aaa/.local/lib/python3.7/site-packages<br />
  </p>
</blockquote>

ということが分かりますので、  
vi .bash_profile  
→追記：port PATH=~/.local/lib/python3.7/site-packages:$PATH  
としても、反応なし。  
結論としては、追記は  
export PATH=~/.local/bin:$PATH  
何のためにパスの確認をしたのか・・・  


<blockquote class="wp-block-quote">
  <p>
    $ aws &#8211;version<br />aws-cli/1.16.92 Python/3.7.2 Darwin/18.2.0 botocore/1.12.82<br />
  </p>
</blockquote>

となりました。

## Amazon ECR 認証

_レジストリの認証_  
<a rel="noreferrer noopener" target="_blank" href="https://docs.aws.amazon.com/ja_jp/AmazonECR/latest/userguide/Registries.html">https://docs.aws.amazon.com/ja_jp/AmazonECR/latest/userguide/Registries.html</a>

<blockquote class="wp-block-quote">
  <p>
    $ aws ecr get-login &#8211;no-include-email<br />You must specify a region. You can also configure your region by running &#8220;aws configure&#8221;.
  </p>
</blockquote>

ということで、先にこちら。  
_AWS CLI の設定_  
<a rel="noreferrer noopener" target="_blank" href="https://docs.aws.amazon.com/ja_jp/cli/latest/userguide/cli-chap-configure.html">https://docs.aws.amazon.com/ja_jp/cli/latest/userguide/cli-chap-configure.html</a>

そして、そのためには  
_最初の IAM 管理者のユーザーおよびグループの作成_  
<a rel="noreferrer noopener" target="_blank" href="https://docs.aws.amazon.com/ja_jp/IAM/latest/UserGuide/getting-started_create-admin-group.html">https://docs.aws.amazon.com/ja_jp/IAM/latest/UserGuide/getting-started_create-admin-group.html</a>

「管理者 IAM ユーザーおよびグループの作成 (コンソール)」まででよいのかな・・・

で、今度はaws ecr get-login &#8211;no-include-emailでログインコマンドが出力されるので、それをコピペして実行すると

<blockquote class="wp-block-quote">
  <p>
    WARNING! Using &#8211;password via the CLI is insecure. Use &#8211;password-stdin.<br />Login Succeeded<br />
  </p>
</blockquote>

となります。

## リポジトリにイメージ登録

この状態で手順の2.でリポジトリを作っておき、4.でpush。  
リポジトリ作る時にリージョン指定間違えないように（間違えました）。

さあ、これならpullできるでしょう！（続く）



<div class="kaerebalink-box" style="text-align:left;padding-bottom:20px;font-size:small;zoom: 1;overflow: hidden;">
  <div class="kaerebalink-image" style="float:left;margin:0 15px 10px 0;">
    <a href="//af.moshimo.com/af/c/click?a_id=1238335&#038;p_id=54&#038;pc_id=54&#038;pl_id=616&#038;s_v=b5Rz2P0601xu&#038;url=https%3A%2F%2Fproduct.rakuten.co.jp%2Fproduct%2F-%2F53f3b094ae4a2205124687b0abf3a8d0%2F" target="_blank" ><img src="https://i1.wp.com/thumbnail.image.rakuten.co.jp/ran/img/2001/0009/784/295/005/490/20010009784295005490_1.jpg?ssl=1" style="border: none;" data-recalc-dims="1" /></a><img src="//i.moshimo.com/af/i/impression?a_id=1238335&#038;p_id=54&#038;pc_id=54&#038;pl_id=616" width="1" height="1" style="border:none;" />
  </div>
  
  <div class="kaerebalink-info" style="line-height:120%;zoom: 1;overflow: hidden;">
    <div class="kaerebalink-name" style="margin-bottom:10px;line-height:120%">
      <a href="//af.moshimo.com/af/c/click?a_id=1238335&#038;p_id=54&#038;pc_id=54&#038;pl_id=616&#038;s_v=b5Rz2P0601xu&#038;url=https%3A%2F%2Fproduct.rakuten.co.jp%2Fproduct%2F-%2F53f3b094ae4a2205124687b0abf3a8d0%2F" target="_blank" >徹底攻略ＡＷＳ認定ソリューションアーキテクトアソシエイト教科書 /インプレス/鳥谷部昭寛</a><img src="//i.moshimo.com/af/i/impression?a_id=1238335&#038;p_id=54&#038;pc_id=54&#038;pl_id=616" width="1" height="1" style="border:none;" />
      <div class="kaerebalink-powered-date" style="font-size:8pt;margin-top:5px;font-family:verdana;line-height:120%">
        posted with <a href="https://kaereba.com" rel="nofollow" target="_blank">カエレバ</a>
      </div>
    </div>
    <div class="kaerebalink-detail" style="margin-bottom:5px;">
    </div>
    <div class="kaerebalink-link1" style="margin-top:10px;">
      <div class="shoplinkrakuten" style="display:inline;margin-right:5px">
        <a href="//af.moshimo.com/af/c/click?a_id=1238335&#038;p_id=54&#038;pc_id=54&#038;pl_id=616&#038;s_v=b5Rz2P0601xu&#038;url=https%3A%2F%2Fsearch.rakuten.co.jp%2Fsearch%2Fmall%2FAWS%25E8%25AA%258D%25E5%25AE%259A%2F-%2Ff.1-p.1-s.1-sf.0-st.A-v.2%3Fx%3D0" target="_blank" >楽天市場</a><img src="//i.moshimo.com/af/i/impression?a_id=1238335&#038;p_id=54&#038;pc_id=54&#038;pl_id=616" width="1" height="1" style="border:none;" />
      </div>
      <div class="shoplinkamazon" style="display:inline;margin-right:5px">
        <a href="//af.moshimo.com/af/c/click?a_id=1238337&#038;p_id=170&#038;pc_id=185&#038;pl_id=4062&#038;s_v=b5Rz2P0601xu&#038;url=https%3A%2F%2Fwww.amazon.co.jp%2Fgp%2Fsearch%3Fkeywords%3DAWS%25E8%25AA%258D%25E5%25AE%259A%26__mk_ja_JP%3D%25E3%2582%25AB%25E3%2582%25BF%25E3%2582%25AB%25E3%2583%258A" target="_blank" >Amazon</a><img src="//i.moshimo.com/af/i/impression?a_id=1238337&#038;p_id=170&#038;pc_id=185&#038;pl_id=4062" width="1" height="1" style="border:none;" />
      </div>
      <div class="shoplinkseven" style="display:inline;margin-right:5px">
        <a href="//af.moshimo.com/af/c/click?a_id=1238336&#038;p_id=932&#038;pc_id=1188&#038;pl_id=12456&#038;s_v=b5Rz2P0601xu&#038;url=http%3A%2F%2F7net.omni7.jp%2Fsearch%2F%3Fkeyword%3DAWS%25E8%25AA%258D%25E5%25AE%259A%26searchKeywordFlg%3D1" target="_blank" ><img src="//i.moshimo.com/af/i/impression?a_id=1238336&p_id=932&pc_id=1188&pl_id=12456" width="1" height="1" style="border:none;">7net</a>
      </div>
    </div>
  </div>
  
  <div class="booklink-footer" style="clear: left">
  </div>
</div>