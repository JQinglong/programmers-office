---
title: Code4StartUp ～ UberEatsを作ろう ～ 詳細画面からショッピングカート
author: KONNO Kiyotaka
type: post
date: 2018-12-31T00:24:58+00:00
excerpt: |
  リスト画面から詳細画面呼び出し、そこからショッピングカート（この講座ではTrayという言葉）への追加。
  途中のミニ講座は、「pyramid if」。
archives:
    - 2018
url: /code4startup-～-ubereatsを作ろう-～-詳細画面からショッピングカ/
featured_image: /wp-content/uploads/2018/12/Code4Startup.jpg
post_views_count:
  - 567
categories:
  - プログラミング
  - 書籍
tags:
  - Code4Startup

---
<img class="wp-image-2504 jetpack-lazy-image jetpack-lazy-image--handled" src="https://i2.wp.com/www.programmers-office.ml/wp-content/uploads/2018/12/Code4Startup.jpg?ssl=1" sizes="(max-width: 800px) 100vw, 800px" srcset="https://i2.wp.com/www.programmers-office.ml/wp-content/uploads/2018/12/Code4Startup.jpg?w=800&ssl=1 800w, https://i2.wp.com/www.programmers-office.ml/wp-content/uploads/2018/12/Code4Startup.jpg?resize=300%2C159&ssl=1 300w, https://i2.wp.com/www.programmers-office.ml/wp-content/uploads/2018/12/Code4Startup.jpg?resize=768%2C408&ssl=1 768w" alt="" data-recalc-dims="1" data-lazy-loaded="1" /><a href="https://code4startup.com/?ref=kiyotakakonno" target="_blank" rel="noreferrer noopener">Code4Startup</a>

リスト画面から詳細画面呼び出し、そこからショッピングカート（この講座ではTrayという言葉）への追加。  
途中のミニ講座は、「pyramid if」。  
pyramid ifで調べても何も出てこないので、この講座独特の言葉でしょうか。しかし、「Pyramid of doom」という言葉はあるようです。  
<a href="https://en.wikipedia.org/wiki/Pyramid_of_doom_(programming)" target="_blank" rel="nofollow noopener">https://en.wikipedia.org/wiki/Pyramid_of_doom_(programming)</a>  
簡単に言えば、過剰な入れ子（ネスト）構造でしょうか。そこでなぜ「doom」なのかはやはり不明。  
そして、ifの多重入れ子回避の対応として、Swiftでは「guard」があるよ、というお話です。  
そして、この「ガード節による入れ子条件記述の置き換え」という方法は、ファウラー「リファクタリング プログラミングの体質改善テクニック」からきているのですか・・・。大昔に読んだ・・・

&nbsp;

<div class="kaerebalink-box" style="text-align:left;padding-bottom:20px;font-size:small;zoom: 1;overflow: hidden;">
  <div class="kaerebalink-image" style="float:left;margin:0 15px 10px 0;">
    <a href="//af.moshimo.com/af/c/click?a_id=1238337&#038;p_id=170&#038;pc_id=185&#038;pl_id=4062&#038;s_v=b5Rz2P0601xu&#038;url=https%3A%2F%2Fwww.amazon.co.jp%2Fexec%2Fobidos%2FASIN%2F4894712288%2Fref%3Dnosim" target="_blank" ><img src="https://i0.wp.com/images-fe.ssl-images-amazon.com/images/I/51885S48YPL._SL160_.jpg?ssl=1" style="border: none;" data-recalc-dims="1" /></a><img src="//i.moshimo.com/af/i/impression?a_id=1238337&#038;p_id=170&#038;pc_id=185&#038;pl_id=4062" width="1" height="1" style="border:none;" />
  </div>
  
  <div class="kaerebalink-info" style="line-height:120%;zoom: 1;overflow: hidden;">
    <div class="kaerebalink-name" style="margin-bottom:10px;line-height:120%">
      <a href="//af.moshimo.com/af/c/click?a_id=1238337&#038;p_id=170&#038;pc_id=185&#038;pl_id=4062&#038;s_v=b5Rz2P0601xu&#038;url=https%3A%2F%2Fwww.amazon.co.jp%2Fexec%2Fobidos%2FASIN%2F4894712288%2Fref%3Dnosim" target="_blank" >リファクタリング―プログラムの体質改善テクニック (Object Technology Series)</a><img src="//i.moshimo.com/af/i/impression?a_id=1238337&#038;p_id=170&#038;pc_id=185&#038;pl_id=4062" width="1" height="1" style="border:none;" />
      <div class="kaerebalink-powered-date" style="font-size:8pt;margin-top:5px;font-family:verdana;line-height:120%">
        posted with <a href="https://kaereba.com" rel="nofollow" target="_blank">カエレバ</a>
      </div>
    </div>
    <div class="kaerebalink-detail" style="margin-bottom:5px;">
      マーチン ファウラー ピアソンエデュケーション 2000-05
    </div>
    <div class="kaerebalink-link1" style="margin-top:10px;">
      <div class="shoplinkamazon" style="display:inline;margin-right:5px">
        <a href="//af.moshimo.com/af/c/click?a_id=1238337&#038;p_id=170&#038;pc_id=185&#038;pl_id=4062&#038;s_v=b5Rz2P0601xu&#038;url=https%3A%2F%2Fwww.amazon.co.jp%2Fgp%2Fsearch%3Fkeywords%3D%25E3%2583%25AA%25E3%2583%2595%25E3%2582%25A1%25E3%2582%25AF%25E3%2582%25BF%25E3%2583%25AA%25E3%2583%25B3%25E3%2582%25B0%26__mk_ja_JP%3D%25E3%2582%25AB%25E3%2582%25BF%25E3%2582%25AB%25E3%2583%258A" target="_blank" >Amazon</a><img src="//i.moshimo.com/af/i/impression?a_id=1238337&#038;p_id=170&#038;pc_id=185&#038;pl_id=4062" width="1" height="1" style="border:none;" />
      </div>
      <div class="shoplinkrakuten" style="display:inline;margin-right:5px">
        <a href="//af.moshimo.com/af/c/click?a_id=1238335&#038;p_id=54&#038;pc_id=54&#038;pl_id=616&#038;s_v=b5Rz2P0601xu&#038;url=https%3A%2F%2Fsearch.rakuten.co.jp%2Fsearch%2Fmall%2F%25E3%2583%25AA%25E3%2583%2595%25E3%2582%25A1%25E3%2582%25AF%25E3%2582%25BF%25E3%2583%25AA%25E3%2583%25B3%25E3%2582%25B0%2F-%2Ff.1-p.1-s.1-sf.0-st.A-v.2%3Fx%3D0" target="_blank" >楽天市場</a><img src="//i.moshimo.com/af/i/impression?a_id=1238335&#038;p_id=54&#038;pc_id=54&#038;pl_id=616" width="1" height="1" style="border:none;" />
      </div>
      <div class="shoplinkseven" style="display:inline;margin-right:5px">
        <a href="//af.moshimo.com/af/c/click?a_id=1238336&#038;p_id=932&#038;pc_id=1188&#038;pl_id=12456&#038;s_v=b5Rz2P0601xu&#038;url=http%3A%2F%2F7net.omni7.jp%2Fsearch%2F%3Fkeyword%3D%25E3%2583%25AA%25E3%2583%2595%25E3%2582%25A1%25E3%2582%25AF%25E3%2582%25BF%25E3%2583%25AA%25E3%2583%25B3%25E3%2582%25B0%26searchKeywordFlg%3D1" target="_blank" ><img src="//i.moshimo.com/af/i/impression?a_id=1238336&p_id=932&pc_id=1188&pl_id=12456" width="1" height="1" style="border:none;">7net</a>
      </div>
    </div>
  </div>
  
  <div class="booklink-footer" style="clear: left">
  </div>
</div>