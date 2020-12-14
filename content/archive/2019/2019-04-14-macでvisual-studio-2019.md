---
title: MacでVisual Studio 2019
author: KONNO Kiyotaka
type: post
date: 2019-04-13T23:47:31+00:00
archives:
    - 2019
url: /macでvisual-studio-2019/
post_views_count:
  - 578
categories:
  - プログラミング
tags:
  - Xamarin

---
Visual Studio 2019がリリースされ、Mac版にも対応されていますので、インストールしてみます。

最初にメッセージが出ますが、インストール中2、３回パスワード入力が必要ですので、完全放置はできませんでした。

インストールしたら、サンプルとして  
<a rel="noreferrer noopener" target="_blank" href="https://docs.microsoft.com/ja-jp/xamarin/cross-platform/samples/">https://docs.microsoft.com/ja-jp/xamarin/cross-platform/samples/</a>  
Acquaint  
⁨app-acquaint⁩/App⁩/Acquaint.XForms.sln  
を開きますが、UWPは対応していないというメッセーが出るので、ソリューションからは削除します。<figure class="wp-block-image">

<img src="https://i0.wp.com/www.programmers-office.ml/wp-content/uploads/2019/04/0OUZW.png?resize=300%2C240&#038;ssl=1" alt="" class="wp-image-2857" srcset="https://i0.wp.com/www.programmers-office.ml/wp-content/uploads/2019/04/0OUZW.png?resize=300%2C240&ssl=1 300w, https://i0.wp.com/www.programmers-office.ml/wp-content/uploads/2019/04/0OUZW.png?w=738&ssl=1 738w" sizes="(max-width: 300px) 100vw, 300px" data-recalc-dims="1" /> </figure> 

で、左上に「Xcode 10.2でコマンドラインツールがありません」というメッセージが出ているので、これはインストールしてしまいます。  
<a rel="noreferrer noopener" target="_blank" href="https://developer.apple.com/download/more/">https://developer.apple.com/download/more/</a><figure class="wp-block-image">

<img src="https://i1.wp.com/www.programmers-office.ml/wp-content/uploads/2019/04/スクリーンショット-2019-04-14-7.34.31.png?ssl=1" alt="" class="wp-image-2856" srcset="https://i1.wp.com/www.programmers-office.ml/wp-content/uploads/2019/04/スクリーンショット-2019-04-14-7.34.31.png?w=800&ssl=1 800w, https://i1.wp.com/www.programmers-office.ml/wp-content/uploads/2019/04/スクリーンショット-2019-04-14-7.34.31.png?resize=300%2C230&ssl=1 300w, https://i1.wp.com/www.programmers-office.ml/wp-content/uploads/2019/04/スクリーンショット-2019-04-14-7.34.31.png?resize=768%2C588&ssl=1 768w" sizes="(max-width: 800px) 100vw, 800px" data-recalc-dims="1" /> </figure> 

次に、「アクティブな構成内でプロジェクトがビルドされていません」というメッセージが出て、ビルドが完了しませんが、これは下記が参考になりました。  
<a rel="noreferrer noopener" target="_blank" href="http://kuxumarin.hatenablog.com/entry/2016/12/01/Xamarin.iOS_%E3%81%AE%E3%83%97%E3%83%AD%E3%82%B8%E3%82%A7%E3%82%AF%E3%83%88%E3%81%A7_%22%E3%82%A2%E3%82%AF%E3%83%86%E3%82%A3%E3%83%96%E3%81%AA%E6%A7%8B%E6%88%90%E5%86%85%E3%81%A7%E3%83%97%E3%83%AD">http://kuxumarin.hatenablog.com/entry/2016/12/01/Xamarin.iOS_%E3%81%AE%E3%83%97%E3%83%AD%E3%82%B8%E3%82%A7%E3%82%AF%E3%83%88%E3%81%A7_%22%E3%82%A2%E3%82%AF%E3%83%86%E3%82%A3%E3%83%96%E3%81%AA%E6%A7%8B%E6%88%90%E5%86%85%E3%81%A7%E3%83%97%E3%83%AD</a><figure class="wp-block-image">

<img src="https://i1.wp.com/www.programmers-office.ml/wp-content/uploads/2019/04/HHAJG.png?resize=300%2C199&#038;ssl=1" alt="" class="wp-image-2858" srcset="https://i1.wp.com/www.programmers-office.ml/wp-content/uploads/2019/04/HHAJG.png?resize=300%2C199&ssl=1 300w, https://i1.wp.com/www.programmers-office.ml/wp-content/uploads/2019/04/HHAJG.png?resize=768%2C509&ssl=1 768w, https://i1.wp.com/www.programmers-office.ml/wp-content/uploads/2019/04/HHAJG.png?resize=480%2C320&ssl=1 480w, https://i1.wp.com/www.programmers-office.ml/wp-content/uploads/2019/04/HHAJG.png?w=912&ssl=1 912w" sizes="(max-width: 300px) 100vw, 300px" data-recalc-dims="1" /> </figure> 

ビルドするとそれでも警告は残っていますが、実行すると、何も設定をしていないのでさすがにデータ保存はできませんが、とりあえず、最初の画面表示はできました。<figure class="wp-block-image">

<img src="https://i2.wp.com/www.programmers-office.ml/wp-content/uploads/2019/04/rnbSi.png?fit=1024%2C694&ssl=1" alt="" class="wp-image-2859" srcset="https://i0.wp.com/www.programmers-office.ml/wp-content/uploads/2019/04/rnbSi.png?w=2946&ssl=1 2946w, https://i0.wp.com/www.programmers-office.ml/wp-content/uploads/2019/04/rnbSi.png?resize=300%2C203&ssl=1 300w, https://i0.wp.com/www.programmers-office.ml/wp-content/uploads/2019/04/rnbSi.png?resize=768%2C520&ssl=1 768w, https://i0.wp.com/www.programmers-office.ml/wp-content/uploads/2019/04/rnbSi.png?resize=1024%2C694&ssl=1 1024w, https://i0.wp.com/www.programmers-office.ml/wp-content/uploads/2019/04/rnbSi.png?w=2000&ssl=1 2000w" sizes="(max-width: 1000px) 100vw, 1000px" /> </figure> <figure class="wp-block-image"><img src="https://i2.wp.com/www.programmers-office.ml/wp-content/uploads/2019/04/スクリーンショット-2019-04-14-8.17.04.png?ssl=1" alt="" class="wp-image-2855" srcset="https://i2.wp.com/www.programmers-office.ml/wp-content/uploads/2019/04/スクリーンショット-2019-04-14-8.17.04.png?w=357&ssl=1 357w, https://i2.wp.com/www.programmers-office.ml/wp-content/uploads/2019/04/スクリーンショット-2019-04-14-8.17.04.png?resize=167%2C300&ssl=1 167w" sizes="(max-width: 357px) 100vw, 357px" data-recalc-dims="1" /></figure>