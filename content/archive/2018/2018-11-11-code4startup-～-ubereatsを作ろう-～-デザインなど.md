---
title: Code4StartUp ～ UberEatsを作ろう ～ デザインなど
author: KONNO Kiyotaka
type: post
date: 2018-11-11T01:59:59+00:00
url: /code4startup-～-ubereatsを作ろう-～-デザインなど/
post_views_count:
  - 914
categories:
  - プログラミング
tags:
  - Code4Startup

---
<a href="https://code4startup.com/?ref=kiyotakakonno" target="_blank" rel="noopener">Code4Startup</a>

Task 16終了。

最後は、デザインの統一等を行いますが。

UIApplication.shared.statusBarStyle = .lightContent  
は、Setter for &#8216;statusBarStyle&#8217; was deprecated in iOS 9.0: Use -[UIViewController preferredStatusBarStyle]  
という警告が出ます。しかし、  
UIApplication.shared.preferredStatusBarStyle = .lightContent  
はダメです。これはこのままにしておきます。

また、  
UINavigationBar<span class="s1">.</span><span class="s2">appearance</span><span class="s1">().</span>titleTextAttributes  
<span class="s1"><span class="Apple-converted-space">            </span>= [NSForegroundColorAtrributeName</span><span class="s1">: </span>UIColor<span class="s1">.</span>white<span class="s1">]<br /> はエラーとなり、コメント欄では、[NSAttributedStringKey.</span>foregroundColor<span class="s1">: </span>UIColor<span class="s1">.</span>white<span class="s1">]<br /> </span><span class="s1">にしたら良いというコメントがあるのですが、正しくは、<br /> </span><span class="s1">[</span>NSAttributedString<span class="s1">.</span>Key<span class="s1">.</span>foregroundColor<span class="s1">: </span>UIColor<span class="s1">.</span>white<span class="s1">]でした。</span>

また、色選択の支援Webサービスが紹介されています。  
<a href="http://uicolor.xyz/#/hex-to-ui" target="_blank" rel="noopener">http://uicolor.xyz/#/hex-to-ui</a>

<span class="s1"><a href="https://code4startup.com/?ref=kiyotakakonno" target="_blank" rel="noopener">Code4Startup</a><br /> </span>