---
title: Vue JS Crash Course
author: KONNO Kiyotaka
type: post
date: 2020-04-18T07:40:45+00:00
archives:
    - 2020
url: /vue-js-crash-course/
featured_image: /wp-content/uploads/2020/04/スクリーンショット-2020-04-17-11.16.20.png
post_views_count:
  - 212
categories:
  - プログラミング
tags:
  - Vue

---
こちらのコースをやってみました。以下、単なるメモです。

Vue JS Crash Course<figure class="wp-block-embed-youtube wp-block-embed is-type-video is-provider-youtube wp-embed-aspect-16-9 wp-has-aspect-ratio">

<div class="wp-block-embed__wrapper">
  <span class="embed-youtube" style="text-align:center; display: block;"></span>
</div></figure> 

[https://github.com/bradtraversy/vue\_crash\_todolist][1]

node10の頃

Vue CLI インストール

<https://cli.vuejs.org/guide/installation.html>

<pre class="wp-block-code"><code>$ npm install -g @vue/cli
$ vue --version
@vue/cli 4.3.1</code></pre>

4なんだ・・・

<pre class="wp-block-code"><code>$ vue create test
いっぱいエラー出てるけど・・・</code></pre>

<pre class="wp-block-code"><code>$ cd test
$ npm run serve</code></pre>

開きました

<pre class="wp-block-code"><code>cd ..
vue ui</code></pre>

Vue プロジェクトマネージャ 画面が自動で立ち上がる  
http://localhost:8000/project/select

現在のフォルダのまま（testが表示されているフォルダ）  
vue\_crash\_todolist  
他はデフォルト  
↓  
デフォルトプリセット  
↓  
インストール完了すると、「プロジェクト ダッシュボード」ページが表示される

ダッシュボード画面<figure class="wp-block-image size-large">

<img src="https://i0.wp.com/www.programmers-office.ml/wp-content/uploads/2020/04/スクリーンショット-2020-04-17-11.16.20.png?ssl=1" alt="" class="wp-image-3282" srcset="https://i0.wp.com/www.programmers-office.ml/wp-content/uploads/2020/04/スクリーンショット-2020-04-17-11.16.20.png?w=800&ssl=1 800w, https://i0.wp.com/www.programmers-office.ml/wp-content/uploads/2020/04/スクリーンショット-2020-04-17-11.16.20.png?resize=300%2C199&ssl=1 300w, https://i0.wp.com/www.programmers-office.ml/wp-content/uploads/2020/04/スクリーンショット-2020-04-17-11.16.20.png?resize=768%2C510&ssl=1 768w, https://i0.wp.com/www.programmers-office.ml/wp-content/uploads/2020/04/スクリーンショット-2020-04-17-11.16.20.png?resize=480%2C320&ssl=1 480w" sizes="(max-width: 800px) 100vw, 800px" data-recalc-dims="1" /> </figure> 

プロジェクトタスク画面<figure class="wp-block-image size-large">

<img src="https://i1.wp.com/www.programmers-office.ml/wp-content/uploads/2020/04/スクリーンショット-2020-04-17-11.19.51.png?ssl=1" alt="" class="wp-image-3283" srcset="https://i1.wp.com/www.programmers-office.ml/wp-content/uploads/2020/04/スクリーンショット-2020-04-17-11.19.51.png?w=800&ssl=1 800w, https://i1.wp.com/www.programmers-office.ml/wp-content/uploads/2020/04/スクリーンショット-2020-04-17-11.19.51.png?resize=300%2C198&ssl=1 300w, https://i1.wp.com/www.programmers-office.ml/wp-content/uploads/2020/04/スクリーンショット-2020-04-17-11.19.51.png?resize=768%2C508&ssl=1 768w" sizes="(max-width: 800px) 100vw, 800px" data-recalc-dims="1" /> </figure> 

main.js がエントリポイント

アロー関数（=>）の復習などしながら（けど、render: h => h(App)　はやはり難しいと思ったら下記でなんとなく分かった！）、App.vue の仕組みの説明。  
[Vue.jsのrender: h => h(App)について調べた][2]

style記述は、上記のgithubからもらってくる。

Component「Todos.vue」を作って、App.vueで読み込む。

v-bind  
<a href="https://jp.vuejs.org/v2/guide/class-and-style.html" target="_blank" aria-label=" (opens in a new tab)" rel="noreferrer noopener" class="aioseop-link">https://jp.vuejs.org/v2/guide/class-and-style.html</a>

<https://jp.vuejs.org/v2/api/#v-bind>

もっと基礎の勉強はこちらの方が良い？

<https://vueschool.io/courses/vuejs-fundamentals>

emitの意味は発射！

App.vue

<pre class="wp-block-code"><code>36: this.todos = this.todos.filter(todo => tood.id != id);
  36:38  error  'todo' is defined but never used  no-unused-vars
  36:46  error  'tood' is not defined             no-undef</code></pre>

解消しなかった

[JSONPlaceholder][3]  
今回はこれが使える

<https://jsonplaceholder.typicode.com/todos>

npm i axios

やはり本当の初心者向けではないかな。

 [1]: https://github.com/bradtraversy/vue_crash_todolist
 [2]: https://qiita.com/teinen_qiita/items/ed1bb1909a17f9ca9daa
 [3]: https://jsonplaceholder.typicode.com/