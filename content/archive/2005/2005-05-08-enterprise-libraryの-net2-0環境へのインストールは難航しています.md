---
title: Enterprise Libraryの.NET2.0環境へのインストールは難航しています
type: post
date: 2005-05-07T18:14:16+00:00
archives:
    - 2005
url: /enterprise-libraryの-net2-0環境へのインストールは難航しています/
post_views_count:
  - 89

---
Enterprise Libraryを.NET2.0環境で使ってみようと思いましたが、一筋縄ではいきませんでした。  
何はともあれ、こちらからダウンロードできる最新版をインストールします。  
<http://www.microsoft.com/downloads/details.aspx?FamilyId=0325B97A-9534-4349-8038-D56B38EC394C&displaylang=en>  
現時点ではEnterpriseLibraryJan2005.exeを使っています。  
Enterprise Libraryはそれぞれがnunit.frameworkを参照していますので、前もってにNUnitのインストールも必要です。  
<http://www.nunit.org/>  
現時点では2.2.0を使っています。  
私の環境では、VS2003は入っていないので、おもむろに、  
インストール先\src\EnterpriseLibrary.sln  
をダブルクリックすると、変換ウィザードが走ります。  
変換後、さらにおもむろにビルドしてみると、悲しいことにそのままではビルドできません。  
エラー 1 エラーとしての警告: &#8216;System.Collections.IHashCodeProvider&#8217; は古い形式です: &#8216;Please use IEqualityComparer instead.&#8217; D:\Program Files\Microsoft Enterprise Library\src\Common\DataCollection.cs 32 35 Common  
といった感じで、「古い形式です」のエラーが相当数出ています。  
これをメッセージにしたがってIEqualityComparerに変更すると、今度は  
エラー 10 引数 &#8216;1&#8217;: &#8216;System.Collections.IEqualityComparer&#8217; から &#8216;int&#8217; に変換できません。 D:\Program Files\Microsoft Enterprise Library\src\Common\DataCollection.cs 662 42 Common  
などが出てきて、収拾がつかなくなります。  
そんな状況なので、後日再チャレンジはしたいと思いますが、チャレンジする方はいっぺんにやらないで一つずつやるか、2003でビルドしたものを使うほうがよいのかもしれません。