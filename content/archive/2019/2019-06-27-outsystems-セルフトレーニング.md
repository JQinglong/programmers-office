---
title: OutSystems セルフトレーニング
author: KONNO Kiyotaka
type: post
date: 2019-06-27T12:07:25+00:00
url: /outsystems-セルフトレーニング/
featured_image: /wp-content/uploads/2019/06/20190616_231627.jpg
post_views_count:
  - 904
categories:
  - プログラミング
tags:
  - OutSystems

---
OutSystemsもおもしろうそうなので、早速、WebAPIのデータを表示させるアプリを作ってみようかと思います。

その際、mac版を使ったところ、読み込み時にエラーになってしまう。Windows版では成功したということは、やはりmac版は多少不安定な面がるかもしれません。

そして、呼び出しはできる（WebAPI読み込みコンポーネントのようなものは作れる）ものの、それを画面のListに表示させる方法がいまいちわからない。

もう少し勉強しようということで、こちらをしばらくやってみたいと思います。

OutSystems セルフトレーニング

[http://www.bluememe.jp/outsystems/outsystems\_support/self\_training.html][1]

（しばらくこのページを随時更新していく形になります）

## 1　コースイントロダクション

日本語字幕あり（しばらくあるようなので、特筆しない限りは以降、日本語字幕ありです）  
各セッションの概要  
どういうアプリを作っていくか  
　映画管理  
　ホテル予約  
試験制度  
　どんな問題が出るか

## 2　OutSystemsの基礎知識

### 2.1　OutSystems概要

development  
quality  
production  
プラットフォームサーバ  
　コンパイル  
　デプロイ  
　管理  
　service studio  
　integration studio  
　service center

### 2.2　Service Studioとは

ここで使われているのはバージョン10  
基本的なIDE機能は概ね予想通り  
最後にソースの競合、マージの説明  
ソース管理ツールも統合されているイメージ

## 3　ウェブアプリ開発の基礎

### 3.1　画面のライフサイクル

Webアプリケーションとは何か  
ブラウザは何をするのか  
静的リソースと動的コンテンツ  
Preparationという概念を使用しており、その中でデータ取得等を行う

### 3.2　データのモデリング

Entity→テーブルの行  
　Attribute→列  
Service Studioのデータレイヤーで作成  
名前からデータ型を推測してテーブルを作る！  
例：Amount→Currency

### 3.3　データのモデリングをしてみよう

これから行うExerciseの説明。（ビデオなし）  
movie databaseのwebアプリケーションを作ります。  
継続的に拡張、公開、テストを行います。  
行う内容は  
1.アプリケーション作成  
2.最初のモジュールの作成  
3.エンティティとbootstrapデータの作成  
4.静的エンティティとレコードの作成  
5.Outsystems webサーバでの公開  
レッスン素材は用意されており、ダウンロードできます。（ログインしていないとダウンロードボタンが表示されません）

レッスン素材の中にテキストのpdfが入っているので、それを見て実施します。45分とのこと。

詳細は別稿。<figure class="wp-block-embed-wordpress wp-block-embed is-type-wp-embed is-provider-programmers-office">

<div class="wp-block-embed__wrapper">
  <blockquote class="wp-embedded-content" data-secret="4A4nKRzoct">
    <a href="https://www.programmers-office.ml/3-3%e3%80%80%e3%83%87%e3%83%bc%e3%82%bf%e3%81%ae%e3%83%a2%e3%83%87%e3%83%aa%e3%83%b3%e3%82%b0%e3%82%92%e3%81%97%e3%81%a6%e3%81%bf%e3%82%88%e3%81%86%ef%bc%88outsystems-%e3%82%bb%e3%83%ab%e3%83%95/">3.3　データのモデリングをしてみよう（OutSystems セルフトレーニング）</a>
  </blockquote>
</div></figure> 

### 3.4　アーキテクチャの基礎

アークテクチャの可視化  
モジュール化プログラミング  
Manage Dependencies ウインドウ＝公開アイテムを持つモジュールリスト  
4レイヤーキャンバス＝OutSystemsにおけるモジュール分割のデファクトの方法  
The OutSystems modularization framework: 4 Layer Canvas  
<a rel="noreferrer noopener" target="_blank" href="https://success.outsystems.com/Support/Enterprise_Customers/Maintenance_and_Operations/Designing_the_architecture_of_your_OutSystems_applications/01_The_4_Layer_Canvas">https://success.outsystems.com/Support/Enterprise_Customers/Maintenance_and_Operations/Designing_the_architecture_of_your_OutSystems_applications/01_The_4_Layer_Canvas</a>

### 3.5　ウィジェット I

Inputもウィジェット  
基本的なウィジェットとして、Expression, Input, Label, Button, Link  
より複雑な情報のI/O  
レイアウトウィジェット：Container, Table  
レコードウィジェット：Form, Table Record

### 3.6　ウィジェットを使ってみよう

Exercise  
1.アプリケーションにUIモジュールを追加  
2.コアモジュールに作成されたエンティティの参照  
3.メインエンティティに対するリストと詳細画面の作成  
4.トップメニューの追加  
5.公開とUIモジュールのテスト

詳細は別稿<figure class="wp-block-embed-wordpress wp-block-embed is-type-wp-embed is-provider-programmers-office">

<div class="wp-block-embed__wrapper">
  <blockquote class="wp-embedded-content" data-secret="ldyOWDnkYW">
    <a href="https://www.programmers-office.ml/3-6%e3%80%80%e3%82%a6%e3%82%a3%e3%82%b8%e3%82%a7%e3%83%83%e3%83%88%e3%82%92%e4%bd%bf%e3%81%a3%e3%81%a6%e3%81%bf%e3%82%88%e3%81%86%ef%bc%88outsystems-%e3%82%bb%e3%83%ab%e3%83%95%e3%83%88%e3%83%ac/">3.6　ウィジェットを使ってみよう（OutSystems セルフトレーニング）</a>
  </blockquote>
</div></figure> 

## 4　UIの基礎

### 4.1　リレーションのモデリング

一般論としてのキー  
OutSystemsでは、自動生成の単純キー  
拡張パターン、マスタ/詳細パターン、ジャンクションエンティティ（多対多のための関連テーブル）  
インデックス

### 4.2　リレーションのモデリングをしてみよう

Exercise  
1.エンティティのIDについて  
2.エンティティ間の依存関係作成  
3.二つのエンティティ間の単純リレーション作成  
4.多対多リレーションの作成  
5.エンティティ図の作成  
6.公開  
20分の見込み

詳細は別稿<figure class="wp-block-embed-wordpress wp-block-embed is-type-wp-embed is-provider-programmers-office">

<div class="wp-block-embed__wrapper">
  <blockquote class="wp-embedded-content" data-secret="kVSImpmas4">
    <a href="https://www.programmers-office.ml/4-2%e3%80%80%e3%83%aa%e3%83%ac%e3%83%bc%e3%82%b7%e3%83%a7%e3%83%b3%e3%81%ae%e3%83%a2%e3%83%87%e3%83%aa%e3%83%b3%e3%82%b0%e3%82%92%e3%81%97%e3%81%a6%e3%81%bf%e3%82%88%e3%81%86%ef%bc%88outsystems/">4.2　リレーションのモデリングをしてみよう（OutSystems セルフトレーニング）</a>
  </blockquote>
</div></figure> 

### 4.3　画面のライフサイクル: インタラクション

Navigateという概念の解説  
Endノード、Destinationノード

### 4.4　画面のライフサイクル: インタラクションのエクササイズ

Exercise  
1.画面へのボタンの追加、クリックアクションの実行  
2.画面アクションへのレコード追加・更新処理の追加  
3.ムービー詳細画面へのジャンルカテゴリ化の追加  
4.複数映画、関係者情報の追加、更新

詳細は別稿<figure class="wp-block-embed-wordpress wp-block-embed is-type-wp-embed is-provider-programmers-office">

<div class="wp-block-embed__wrapper">
  <blockquote class="wp-embedded-content" data-secret="ZNclMvU8mu">
    <a href="https://www.programmers-office.ml/4-4%e3%80%80%e7%94%bb%e9%9d%a2%e3%81%ae%e3%83%a9%e3%82%a4%e3%83%95%e3%82%b5%e3%82%a4%e3%82%af%e3%83%ab-%e3%82%a4%e3%83%b3%e3%82%bf%e3%83%a9%e3%82%af%e3%82%b7%e3%83%a7%e3%83%b3%e3%81%ae%e3%82%a8/">4.4　画面のライフサイクル: インタラクションのエクササイズ（OutSystems セルフトレーニング）</a>
  </blockquote>
</div></figure> 

### 4.5　デバッグとモニタリング

デバッグとは  
変数等の値参照機能  
モニタリング機能＝ログレポート

## 5　ビジネスロジックの開発

### 5.1　データのクエリ

AggregatesとSQL Queries  
ここまで見て思った。OutSystemsは現代のAccessか。

### 5.2　ウィジェット II

ComboBoxを中心に、複数の値選択系  
・・・これはComboBoxではなくてドロップダウンリストなのでは？？

### 5.3　データのクエリとウィジェットのエクササイズ

Exercise　100分！  
1.ムービーに参加者を追加するロジックを持つ画面の作成  
2.ムービー参加者を取得する、アグリゲートとSQLクエリーの使用  
3.ムービー詳細としてロールによる参加者の表示  
4.ムービリストへの検索・フィルタ機能の追加

詳細は別稿<figure class="wp-block-embed-wordpress wp-block-embed is-type-wp-embed is-provider-programmers-office">

<div class="wp-block-embed__wrapper">
  <blockquote class="wp-embedded-content" data-secret="zI0YfUjqXF">
    <a href="https://www.programmers-office.ml/5-3%e3%80%80%e3%83%87%e3%83%bc%e3%82%bf%e3%81%ae%e3%82%af%e3%82%a8%e3%83%aa%e3%81%a8%e3%82%a6%e3%82%a3%e3%82%b8%e3%82%a7%e3%83%83%e3%83%88%e3%81%ae%e3%82%a8%e3%82%af%e3%82%b5%e3%82%b5%e3%82%a4/">5.3　データのクエリとウィジェットのエクササイズ（OutSystems セルフトレーニング）</a>
  </blockquote>
</div></figure> 

### 5.4　Actionとコードの再利用性

ここで言う再利用性とは、関数化とかスコープの話  
スクリーンアクション　＝画面内  
ユーザアクション　＝共有  
BPTという外部ロジック呼び出し？

### 5.5　Actionとコードを再利用してみよう

Exercise  
1.再利用可能なユーザアクションの作成  
2.while構文を使ったプログラミングによるリストの構築  
3.Functionとして利用可能なアクション  
4.第二のエントリーポイントの作成

詳細は別稿<figure class="wp-block-embed-wordpress wp-block-embed is-type-wp-embed is-provider-programmers-office">

<div class="wp-block-embed__wrapper">
  <blockquote class="wp-embedded-content" data-secret="eeNhBRp6Rk">
    <a href="https://www.programmers-office.ml/5-5%e3%80%80action%e3%81%a8%e3%82%b3%e3%83%bc%e3%83%89%e3%82%92%e5%86%8d%e5%88%a9%e7%94%a8%e3%81%97%e3%81%a6%e3%81%bf%e3%82%88%e3%81%86%ef%bc%88outsystems-%e3%82%bb%e3%83%ab%e3%83%95%e3%83%88%e3%83%ac/">5.5　Actionとコードを再利用してみよう（OutSystems セルフトレーニング）</a>
  </blockquote>
</div></figure> 

### 5.6　Input Validation

組み込みの必須チェックと型チェック以外に、ユーザ定義のバリデーション

### 5.7　Input Validationのエクササイズ

1.クライアントサイドとダーバサイドのバリデーションの学習  
2.既定の、必須チェックと型チェックの学習  
3.コードによるカスタム（ビジネスルール）バリデーション  
4.バリデーション失敗時のフィードバックの返し方

## 6　Ajaxと繰り返し使えるUI

### 6.1　画面のライフサイクル: Ajax

Submit とAjax Submit  
Ajax Refresh をウィジェットに適用する

### 6.2　画面のライフサイクル: Ajaxのエクササイズ

1.Movie詳細画面にサイドバーを追加  
2.サイドバーにコメントリストを表示するようインプットセクションを追加  
3.Ajaxを利用したコメント送信  
4.Ajaxを利用したコメントリストのリフレッシュ

## 7　セキュリティとセッションハンドリング

### 7.1　セキュリティ

HTTPS通信、SQLインジェクション等サービスとして備えている機能  
アクセスコントロールは考えて実装する必要がある  
ユーザーとグループ  
アプリケーションロール

### 7.2　セキュリティのエクササイズ

1.アプリケーションロール作成  
2.ユーザ作成とロール割り当て  
3.ロール特定によるアプリケーションパーツへのアクセス制限  
4.アプリケーションアクセスに対するユーザ特権の検証

エクササイズはちょっと飛ばします。

### 7.3　セッションハンドリング

Webアプリケーションにおけるセッションというもの  
セッション変数とサイトプロパティ

### 7.4　セッションハンドリングのエクササイズ

1.セッション変数とサイトプロパティの作成  
2.アプリケーションロジックでのセッション変数の使用  
3.頻繁に変更されない変数を定義するためのサイトプロパティ使用  
4.サービスセンターを使用したサイトプロパティの変更

## 8　連携

### 8.1　ウェブサービス

SOAPとREST  
ExposeとConsume  
Service Center 機能によるサポート

### 8.2　ウェブサービスのエクササイズ

1.既存のREST APIをどのように統合するか  
2.REST APIを使用した結果表示画面の修正

### 8.3　Integration Studioとは

.NETやJavaで外部モジュールを書くことができ、その際に、インターフェース部分はIntegration Studioで定義することができますよ、言い換えると、インターフェースを定義したら、各IDE用のソリューションファイルを生成するので、VSなりEclipseなりで、実装部分のみ書いてね、という理解でOK？

## 9　高度なUIのパターン

 [1]: http://www.bluememe.jp/outsystems/outsystems_support/self_training.html