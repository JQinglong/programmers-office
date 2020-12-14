---
title: Tuigwaa、Ruby on Rails、そして・・・
type: post
date: 2006-05-06T14:27:45+00:00
archives:
    - 2006
url: /tuigwaa、ruby-on-rails、そして・・・/
post_views_count:
  - 1167

---
そろそろ、GWも締めに入らないと。  
昨日は、Tuigwaa、今日はRuby on Railsを簡単に動かしてみています。  
■Tuigwaa  
<http://tuigwaa.sandbox.seasar.org/>  
インストールは、ダウンロードファイル内のINSTALL.txtよりも、  
<http://tuigwaa.sandbox.seasar.org/start/quickstart_single.html>を参考にしたほうがよさそうです。  
データベースを作りながら画面入力方式を定義しているというあたりが「ユーザ主導型」の理念のための基本コンセプトでしょうか。  
色々やってみたいのですが、来週14日に期待。  
■Ruby on Rails  
[満足せる豚。眠たげなポチ。][1]さんを参考に[Instant Rails][2]をインストール。  
これは簡単！（IISはいったん停止しましょう）  
そして、[task*pad.jp Imitation with Ruby on Rails][3]さんをベースに[10分間で作るRailsアプリケーションをInstant Rails環境で試す][4]さんを参考にしながら、ちょっといじってみました。  
作業は、Iアイコン > Rails Applications > Opne Ruby Console windowで起動するコンソールから。  
rails Taskで、Taskフォルダ以下の階層が作られます。  
次のDB設定は、Instant Rails ではMySQLなので、変更せずそのまま。  
※ここで注目は、development・test・productionの三構成が作られているというところ。参考になります。  
で、DBを作るのは、Iアイコン > Configure > Database ( via phpMyAdmin )のWeb画面から。  
作り終わったらコンソールに戻り、cd Taskの後、ruby script/generate model task、ruby script/generate controller task。  
とりあえず、これでできているようなので、Iアイコン > RailsApplication > Manage Rails Applicationで、Taskにチェックしてstart with WEBrick後ブラウザでhttp://127.0.0.1:3000/Task表示。  
動いているようですが「Unknown action」なので、app\controllers\task_controller.rbにscaffold :taskを追記すると、見事「Listing tasks」と表示されました。  
後は、書いてある通りに書いていけばよいですが（ちょっと時間の部分のテーブルレイアウトを間違えたかもで、一部動きがおかしくなってしまいましたが・・・）、ちょっとづつエラーも出しながら書いていけば、Railsが何をやってくれているかの雰囲気がわかってよいと思います。  
データ追加のメソッドで  
task = Task.new(params[:task])  
・・・  
task.save  
みたいに値が引っ張ってこられるのはよいですね。  
ただ、その分、入力フォーム側で定義を書いてあげなくてはならず、この辺をいかに自動生成してあげるかがポイントではないでしょうか。  
テーマは「自動生成」。さぁ、どうするかな～

 [1]: http://blog.hacklife.net/archives/50190377.html
 [2]: http://instantrails.rubyforge.org/wiki/wiki.pl?Instant_Rails
 [3]: http://wids.net/lib/taskpad_ror.html
 [4]: http://lightson.dip.jp/zope/ZWiki/BookmarkOnInstantRails