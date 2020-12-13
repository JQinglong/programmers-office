---
title: Docker push Google Container Registry 編
author: KONNO Kiyotaka
type: post
date: 2019-01-20T02:07:55+00:00
url: /docker-push-google-container-registry-編/
featured_image: /wp-content/uploads/2019/01/スクリーンショット-2019-01-14-19.23.43.jpg
post_views_count:
  - 541
categories:
  - プログラミング
tags:
  - Docker
  - GCP

---
さらに新しい編。ドカベンか！

<div class="kaerebalink-box" style="text-align:left;padding-bottom:20px;font-size:small;zoom: 1;overflow: hidden;">
  <div class="kaerebalink-image" style="float:left;margin:0 15px 10px 0;">
    <a href="//af.moshimo.com/af/c/click?a_id=1238335&#038;p_id=54&#038;pc_id=54&#038;pl_id=616&#038;s_v=b5Rz2P0601xu&#038;url=https%3A%2F%2Fproduct.rakuten.co.jp%2Fproduct%2F-%2Fae35f90531dfecdf391744054cc0e0bc%2F" target="_blank" ><img src="https://i2.wp.com/thumbnail.image.rakuten.co.jp/ran/img/9001/1001/000/000/087/601/90011001000000087601_1.jpg?ssl=1" style="border: none;" data-recalc-dims="1" /></a><img src="//i.moshimo.com/af/i/impression?a_id=1238335&#038;p_id=54&#038;pc_id=54&#038;pl_id=616" width="1" height="1" style="border:none;" />
  </div>
  
  <div class="kaerebalink-info" style="line-height:120%;zoom: 1;overflow: hidden;">
    <div class="kaerebalink-name" style="margin-bottom:10px;line-height:120%">
      <a href="//af.moshimo.com/af/c/click?a_id=1238335&#038;p_id=54&#038;pc_id=54&#038;pl_id=616&#038;s_v=b5Rz2P0601xu&#038;url=https%3A%2F%2Fproduct.rakuten.co.jp%2Fproduct%2F-%2Fae35f90531dfecdf391744054cc0e0bc%2F" target="_blank" >ドカベン　プロ野球編　（1-52巻 全巻） / 水島新司 / 秋田書店</a><img src="//i.moshimo.com/af/i/impression?a_id=1238335&#038;p_id=54&#038;pc_id=54&#038;pl_id=616" width="1" height="1" style="border:none;" />
      <div class="kaerebalink-powered-date" style="font-size:8pt;margin-top:5px;font-family:verdana;line-height:120%">
        posted with <a href="https://kaereba.com" rel="nofollow" target="_blank">カエレバ</a>
      </div>
    </div>
    <div class="kaerebalink-detail" style="margin-bottom:5px;">
    </div>
    <div class="kaerebalink-link1" style="margin-top:10px;">
      <div class="shoplinkrakuten" style="display:inline;margin-right:5px">
        <a href="//af.moshimo.com/af/c/click?a_id=1238335&#038;p_id=54&#038;pc_id=54&#038;pl_id=616&#038;s_v=b5Rz2P0601xu&#038;url=https%3A%2F%2Fsearch.rakuten.co.jp%2Fsearch%2Fmall%2F%25E3%2583%2589%25E3%2582%25AB%25E3%2583%2599%25E3%2583%25B3%25E3%2580%2580%25E3%2582%25BB%25E3%2583%2583%25E3%2583%2588%2F-%2Ff.1-p.1-s.1-sf.0-st.A-v.2%3Fx%3D0" target="_blank" >楽天市場</a><img src="//i.moshimo.com/af/i/impression?a_id=1238335&#038;p_id=54&#038;pc_id=54&#038;pl_id=616" width="1" height="1" style="border:none;" />
      </div>
      <div class="shoplinkamazon" style="display:inline;margin-right:5px">
        <a href="//af.moshimo.com/af/c/click?a_id=1238337&#038;p_id=170&#038;pc_id=185&#038;pl_id=4062&#038;s_v=b5Rz2P0601xu&#038;url=https%3A%2F%2Fwww.amazon.co.jp%2Fgp%2Fsearch%3Fkeywords%3D%25E3%2583%2589%25E3%2582%25AB%25E3%2583%2599%25E3%2583%25B3%25E3%2580%2580%25E3%2582%25BB%25E3%2583%2583%25E3%2583%2588%26__mk_ja_JP%3D%25E3%2582%25AB%25E3%2582%25BF%25E3%2582%25AB%25E3%2583%258A" target="_blank" >Amazon</a><img src="//i.moshimo.com/af/i/impression?a_id=1238337&#038;p_id=170&#038;pc_id=185&#038;pl_id=4062" width="1" height="1" style="border:none;" />
      </div>
      <div class="shoplinkseven" style="display:inline;margin-right:5px">
        <a href="//af.moshimo.com/af/c/click?a_id=1238336&#038;p_id=932&#038;pc_id=1188&#038;pl_id=12456&#038;s_v=b5Rz2P0601xu&#038;url=http%3A%2F%2F7net.omni7.jp%2Fsearch%2F%3Fkeyword%3D%25E3%2583%2589%25E3%2582%25AB%25E3%2583%2599%25E3%2583%25B3%25E3%2580%2580%25E3%2582%25BB%25E3%2583%2583%25E3%2583%2588%26searchKeywordFlg%3D1" target="_blank" ><img src="//i.moshimo.com/af/i/impression?a_id=1238336&p_id=932&pc_id=1188&pl_id=12456" width="1" height="1" style="border:none;">7net</a>
      </div>
    </div>
  </div>
  
  <div class="booklink-footer" style="clear: left">
  </div>
</div>

今度は、Google Container Registry へのpushを試してみます。

## 始める前の準備

_Container Registry のクイックスタート_  
<a rel="noreferrer noopener" target="_blank" href="https://cloud.google.com/container-registry/docs/quickstart?hl=ja&authuser=0">https://cloud.google.com/container-registry/docs/quickstart?hl=ja</a>

プロジェクトは既存のものを使用します。  
課金の設定もしてあります。  
Container Registry APIの有効化は、こちらのページのリンクボタンからGCP画面へ飛んで行って、ボタンを押していけばできます。  
Google Cloud SDKはインストール済みでしたので、ここもスキップ。  
この時にインストールしたのですね。  
_サイト引っ越し、そして、再引っ越し（Part2）_  
<a rel="noreferrer noopener" target="_blank" href="https://www.programmers-office.ml/2018/12/22/%E3%82%B5%E3%82%A4%E3%83%88%E5%BC%95%E3%81%A3%E8%B6%8A%E3%81%97%E3%80%81%E3%81%9D%E3%81%97%E3%81%A6%E3%80%81%E5%86%8D%E5%BC%95%E3%81%A3%E8%B6%8A%E3%81%97%EF%BC%88part2%EF%BC%89/">https://www.programmers-office.ml/2018/12/22/%E3%82%B5%E3%82%A4%E3%83%88%E5%BC%95%E3%81%A3%E8%B6%8A%E3%81%97%E3%80%81%E3%81%9D%E3%81%97%E3%81%A6%E3%80%81%E5%86%8D%E5%BC%95%E3%81%A3%E8%B6%8A%E3%81%97%EF%BC%88part2%EF%BC%89/</a>

Dockerもインストール済み。ビルド済み。  
認証から行きます。

## 認証してpush

<blockquote class="wp-block-quote">
  <p>
    gcloud auth configure-docker<br />
  </p>
</blockquote>

でDocker config fileへの更新確認をされるので、Yで進めます。

次にイメージにタグをつけます。  
そしてpushしようとすると、認証できていない・・・

<blockquote class="wp-block-quote">
  <p>
    denied: Token exchange failed for project &#8216;xxx&#8217;. Caller does not have permission &#8216;storage.buckets.create&#8217;. To configure permissions, follow instructions at: https://cloud.google.com/container-registry/docs/access-control
  </p>
</blockquote>

バックエンドとして Cloud Storage バケットを使用している、ということで、そちらの設定が必要ということです。  
となると、Always Freeの範囲内かが気になりますが、下記を参照して、リージョンを考えましょう。  
_Cloud Storage の Always Free の使用制限_  
<a rel="noreferrer noopener" target="_blank" href="https://cloud.google.com/storage/pricing?hl=ja&authuser=0">https://cloud.google.com/storage/pricing?hl=ja</a>  
Regionalでus-east1を選択します。

その上で、gsutil lsを叩いて、そのストレージが表示されることを確認します。私の場合、gcloud auth loginで認証をやり直して、gcloud config set project PROJECT_IDでプロジェクトを選択し直して、表示されるようになりました。

そうすると、pushできるようになりました。<figure class="wp-block-image">

<img src="https://i0.wp.com/www.programmers-office.ml/wp-content/uploads/2019/01/スクリーンショット-2019-01-20-10.53.24.png?fit=1024%2C299&ssl=1" alt="" class="wp-image-2712" srcset="https://i0.wp.com/www.programmers-office.ml/wp-content/uploads/2019/01/スクリーンショット-2019-01-20-10.53.24.png?w=2320&ssl=1 2320w, https://i0.wp.com/www.programmers-office.ml/wp-content/uploads/2019/01/スクリーンショット-2019-01-20-10.53.24.png?resize=300%2C88&ssl=1 300w, https://i0.wp.com/www.programmers-office.ml/wp-content/uploads/2019/01/スクリーンショット-2019-01-20-10.53.24.png?resize=768%2C224&ssl=1 768w, https://i0.wp.com/www.programmers-office.ml/wp-content/uploads/2019/01/スクリーンショット-2019-01-20-10.53.24.png?resize=1024%2C299&ssl=1 1024w, https://i0.wp.com/www.programmers-office.ml/wp-content/uploads/2019/01/スクリーンショット-2019-01-20-10.53.24.png?w=2000&ssl=1 2000w" sizes="(max-width: 1000px) 100vw, 1000px" /> </figure> 

pushはできるんですよ、pushは・・・



<div class="kaerebalink-box" style="text-align:left;padding-bottom:20px;font-size:small;zoom: 1;overflow: hidden;">
  <div class="kaerebalink-image" style="float:left;margin:0 15px 10px 0;">
    <a href="//af.moshimo.com/af/c/click?a_id=1238335&#038;p_id=54&#038;pc_id=54&#038;pl_id=616&#038;s_v=b5Rz2P0601xu&#038;url=https%3A%2F%2Fproduct.rakuten.co.jp%2Fproduct%2F-%2F4c3ab5c6faf5e80f0bbc0daa49b2a5a5%2F" target="_blank" ><img src="https://i1.wp.com/thumbnail.image.rakuten.co.jp/ran/img/2001/0009/784/865/941/715/20010009784865941715_1.jpg?ssl=1" style="border: none;" data-recalc-dims="1" /></a><img src="//i.moshimo.com/af/i/impression?a_id=1238335&#038;p_id=54&#038;pc_id=54&#038;pl_id=616" width="1" height="1" style="border:none;" />
  </div>
  
  <div class="kaerebalink-info" style="line-height:120%;zoom: 1;overflow: hidden;">
    <div class="kaerebalink-name" style="margin-bottom:10px;line-height:120%">
      <a href="//af.moshimo.com/af/c/click?a_id=1238335&#038;p_id=54&#038;pc_id=54&#038;pl_id=616&#038;s_v=b5Rz2P0601xu&#038;url=https%3A%2F%2Fproduct.rakuten.co.jp%2Fproduct%2F-%2F4c3ab5c6faf5e80f0bbc0daa49b2a5a5%2F" target="_blank" >Ｇｏｏｇｌｅ　Ｃｌｏｕｄ　Ｐｌａｔｆｏｒｍによる機械学習システム構築 データ処理・学習・運用までをサーバーレスで /リックテレコム/吉川隼人</a><img src="//i.moshimo.com/af/i/impression?a_id=1238335&#038;p_id=54&#038;pc_id=54&#038;pl_id=616" width="1" height="1" style="border:none;" />
      <div class="kaerebalink-powered-date" style="font-size:8pt;margin-top:5px;font-family:verdana;line-height:120%">
        posted with <a href="https://kaereba.com" rel="nofollow" target="_blank">カエレバ</a>
      </div>
    </div>
    <div class="kaerebalink-detail" style="margin-bottom:5px;">
    </div>
    <div class="kaerebalink-link1" style="margin-top:10px;">
      <div class="shoplinkrakuten" style="display:inline;margin-right:5px">
        <a href="//af.moshimo.com/af/c/click?a_id=1238335&#038;p_id=54&#038;pc_id=54&#038;pl_id=616&#038;s_v=b5Rz2P0601xu&#038;url=https%3A%2F%2Fsearch.rakuten.co.jp%2Fsearch%2Fmall%2FGoogle%2520Cloud%2F-%2Ff.1-p.1-s.1-sf.0-st.A-v.2%3Fx%3D0" target="_blank" >楽天市場</a><img src="//i.moshimo.com/af/i/impression?a_id=1238335&#038;p_id=54&#038;pc_id=54&#038;pl_id=616" width="1" height="1" style="border:none;" />
      </div>
      <div class="shoplinkamazon" style="display:inline;margin-right:5px">
        <a href="//af.moshimo.com/af/c/click?a_id=1238337&#038;p_id=170&#038;pc_id=185&#038;pl_id=4062&#038;s_v=b5Rz2P0601xu&#038;url=https%3A%2F%2Fwww.amazon.co.jp%2Fgp%2Fsearch%3Fkeywords%3DGoogle%2520Cloud%26__mk_ja_JP%3D%25E3%2582%25AB%25E3%2582%25BF%25E3%2582%25AB%25E3%2583%258A" target="_blank" >Amazon</a><img src="//i.moshimo.com/af/i/impression?a_id=1238337&#038;p_id=170&#038;pc_id=185&#038;pl_id=4062" width="1" height="1" style="border:none;" />
      </div>
      <div class="shoplinkseven" style="display:inline;margin-right:5px">
        <a href="//af.moshimo.com/af/c/click?a_id=1238336&#038;p_id=932&#038;pc_id=1188&#038;pl_id=12456&#038;s_v=b5Rz2P0601xu&#038;url=http%3A%2F%2F7net.omni7.jp%2Fsearch%2F%3Fkeyword%3DGoogle%2520Cloud%26searchKeywordFlg%3D1" target="_blank" ><img src="//i.moshimo.com/af/i/impression?a_id=1238336&p_id=932&pc_id=1188&pl_id=12456" width="1" height="1" style="border:none;">7net</a>
      </div>
    </div>
  </div>
  
  <div class="booklink-footer" style="clear: left">
  </div>
</div>