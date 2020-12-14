---
title: '[VS2005]LoadComplete　イベント'
type: post
date: 2005-05-29T08:37:56+00:00
archives:
    - 2005
url: /vs2005loadcomplete　イベント/
post_views_count:
  - 83

---
ASP.NET2.0では、PageイベントとしてLoadCompleteイベントが存在します。  
ヘルプによると  
The LoadComplete event occurs at the end of the page load stage. At this point in the page life cycle, all postback data and view state data is loaded into controls on the page. Any new controls created after this event will not be automatically loaded with postback or view state data.  
ということで、これまでPageのLoadイベントとユーザコントロールのLoadイベントの関係が分かりにくいために、思った動きをさせられず悩まされることがありましたが、今回はこのイベント発生時にはポストバックデータが反映されていることを前提にできるので、処理がわかりやすくなりそうです（こういう目的ですから、ascxのPageイベントにはLoadイベントしかありません）。  
いいですね。