---
title: Nuxt JS beginner tutorial
author: KONNO Kiyotaka
type: post
date: 2020-04-17T01:16:53+00:00
archives:
    - 2020
url: /nuxt-js-beginner-tutorial/
featured_image: /wp-content/uploads/2020/04/nuxt-emoji.png
post_views_count:
  - 213
categories:
  - プログラミング
tags:
  - Nuxt.js
  - Vue

---
 <figure class="wp-block-embed-youtube wp-block-embed is-type-video is-provider-youtube wp-embed-aspect-16-9 wp-has-aspect-ratio">

<div class="wp-block-embed__wrapper">
  <span class="embed-youtube" style="text-align:center; display: block;"></span>
</div></figure> 

もう一度、Nuxt の勉強をしようということで、上記チュートリアルを一式やって見ました。単なるメモです。

### 1 Nuxt JS beginner tutorial &#8211; In Depth Intro to Nuxt.js | SPA, SSR, Static Site, Vue.js Family

What is Nuxtjs? Why Nuxt.js is so good? What Nuxt.js can do? What Nuxt.js Includes  
How single page application works?  
How static site generation in nuxt works?  
How universal application is created in nuxtjs?

<hr class="wp-block-separator" />

### 2 Nuxt JS beginner tutorial &#8211; Getting Started with NuxtJs | How to setup Nuxt Project

始める前に、Docker環境を作る

<pre class="wp-block-code"><code>version: '3'

services:
  nuxt-app:
    build: 
      context: ./nuxt-app/
      dockerfile: Dockerfile
    volumes:
      - ./nuxt-app:/usr/src/app
    command: sh -c "npm run dev"
    ports:
      - "8003:3000"</code></pre>

<pre class="wp-block-code"><code>FROM node:13-alpine  

RUN apk add --update alpine-sdk
RUN apk add --no-cache git python g++ make

WORKDIR /usr/src/app</code></pre>

これらを下記構成で用意します。

<pre class="wp-block-code"><code>nuxt-beginner
├── docker-compose.yml
└── nuxt-app
    └── Dockerfile</code></pre>

<pre class="wp-block-code"><code>$ docker-compose build
$ docker-compose run nuxt-app sh

# npm init -y
# npm i nuxt --save</code></pre>

package.json

<pre class="wp-block-code"><code>  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "dev" : "nuxt"
  },</code></pre>

いったんexitしてから

<pre class="wp-block-code"><code> $ docker-compose up -d
 $ docker-compose ps
 $ docker-compose logs -f nuxt-app</code></pre>

http://localhost:8003  
見えない

<pre class="wp-block-code"><code># wget -S --spider http://localhost:3000

Connecting to localhost:3000 (127.0.0.1:3000)
 wget: can't connect to remote host (127.0.0.1): Connection refused</code></pre>

ちょっとうまくいかなかった

<hr class="wp-block-separator" />

### 3 Nuxt JS beginner tutorial &#8211; Create Nuxtjs Project with NPX to have everything on our nuxt app

Dockerfileの階層を一つ上げる

<pre class="wp-block-code"><code>version: '3'

services:
  nuxt-app:
    build: 
      context: ./
      dockerfile: Dockerfile
    volumes:
      - ./nuxt-app:/usr/src/app
    command: sh -c "npm run dev"
    ports:
      - "8003:3000"</code></pre>

<pre class="wp-block-code"><code>nuxt-beginner
├── docker-compose.yml
└── Dockerfile</code></pre>

<pre class="wp-block-code"><code>$ docker-compose build
$ docker-compose run nuxt-app sh

# npm install -g create-nuxt-app
# npx create-nuxt-app nuxt-app

create-nuxt-app v2.15.0
✨  Generating Nuxt.js project in nuxt-app
? Project name nuxt-app
? Project description My good Nuxt.js project
? Author name jqinglong
? Choose programming language TypeScript
? Choose the package manager Npm
? Choose UI framework Vuetify.js
? Choose custom server framework Express
? Choose Nuxt.js modules Axios, Progressive Web App (PWA) Support, DotEnv
? Choose linting tools ESLint, Prettier, Lint staged files, StyleLint
? Choose test framework AVA
? Choose rendering mode Universal (SSR)
? Choose development tools jsconfig.json (Recommended for VS Code)</code></pre>

create-nuxt-appの項目が色々変わっている

しかし、中からも外からもつながらないので、Docker使わず、直接Mac環境で作業します。環境はDockerで作ったけど、そのまま動きました。

<hr class="wp-block-separator" />

### 5 Nuxt JS beginner tutorial &#8211; Understanding Plugins in Nuxtjs

<hr class="wp-block-separator" />

### 6 Nuxt JS beginner tutorial &#8211; Understanding Module in Nuxtjs

<hr class="wp-block-separator" />

### 7 Nuxt JS beginner tutorial | Understanding Nuxtjs Configuration file &#8211; Nuxt.config.js

<hr class="wp-block-separator" />

### 8 Nuxt JS beginner tutorial | Index.html file inside Nuxtjs

ルートディレクトリにapp.htmlを作っておくと、反映される

<hr class="wp-block-separator" />

### 9 Nuxt JS beginner tutorial &#8211; Nuxtjs for everytonDefault Layout

layouts/default.vue の役割

<hr class="wp-block-separator" />

### 10 Nuxt JS beginner tutorial &#8211; create custom layout

scafold効かなくて悲しい。下記をコピペして使います。

<pre class="wp-block-code"><code>&lt;template>
    &lt;div class="">

    &lt;/div>
&lt;/template>

&lt;script lang="ts">
import Vue from 'vue'
export default Vue.extend({

})
&lt;/script>

&lt;style>

&lt;/style></code></pre>

<hr class="wp-block-separator" />

### 11 Nuxt JS beginner tutorial &#8211; Nuxt custom error page

最初から、layouts/error.vueが作られている

<hr class="wp-block-separator" />

### 12 Nuxt JS beginner tutorial &#8211; Nuxt attributes of pages

head  
data  
asyncdata

<hr class="wp-block-separator" />

### 13 Nuxt JS beginner tutorial &#8211; Nuxt meta tag override

hidまで指定すれば上書きになる

<hr class="wp-block-separator" />

### 14 Nuxt JS beginner tutorial &#8211; Nuxt Nuxt link

https://vuetifyjs.com/en/  
からソースをもらってくる

layout/xxx  
に反映

<hr class="wp-block-separator" />

### 15 Nuxt JS beginner tutorial &#8211; Dynamic Routings

pagesの下の階層構造  
_で始まるvue

<hr class="wp-block-separator" />

### 16 Nuxt JS beginner tutorial &#8211; Route params validation

createdフック

<hr class="wp-block-separator" />

### 17 Nuxt JS beginner tutorial &#8211; Nuxt middleware

vueに書くか、nuxt.config.jsに書くか

<https://reqres.in/>

<hr class="wp-block-separator" />

### 18 Nuxt JS beginner tutorial &#8211; Start weather app project

いったん不要なものを消していく  
whether appへのリンク

<hr class="wp-block-separator" />

### 19 Nuxt JS beginner tutorial &#8211; Create Weather app page

Vuetifyのコンポーネントを配置

<hr class="wp-block-separator" />

### 20 Nuxt JS beginner tutorial &#8211; Understand Weather API Website

https://openweathermap.org/api  
サインアップして、API key 取得（メールで送られてくる）

<hr class="wp-block-separator" />

### 21 Nuxt JS beginner tutorial &#8211; Fetch weather data

データ取得してログに出力

<hr class="wp-block-separator" />

### 22 Nuxt JS beginner tutorial &#8211; Dynamic City Weather

入力と連携

<hr class="wp-block-separator" />

### 23 Nuxt JS beginner tutorial &#8211; Show city with weather icon

取得データ表示

<hr class="wp-block-separator" />

### 24 Nuxt JS beginner tutorial &#8211; Show Temperature

<hr class="wp-block-separator" />

### 25 Nuxt JS beginner tutorial &#8211; Show weather description

<hr class="wp-block-separator" />

### 26 Nuxt JS beginner tutorial &#8211; Move to SSR

asyncData

<hr class="wp-block-separator" />

### 27 Nuxt JS beginner tutorial &#8211; Wind & Pressure

その他の情報表示

<hr class="wp-block-separator" />

### 28 Nuxt JS beginner tutorial &#8211; Show Max and Min Temperature

その他の情報表示

<hr class="wp-block-separator" />

### 29 Nuxt JS beginner tutorial &#8211; CleanUp V-If

環境変数に行くかと思ったらやめた

<hr class="wp-block-separator" />

### 30 Nuxt JS beginner tutorial &#8211; Use Dotenv Module

npm i @nuxtjs/dotenv  
nuxt.config.js  
と思ったら入っていたっぽい

.envファイルも存在する

以上で終了<figure class="wp-block-image size-large">

<img src="https://i0.wp.com/www.programmers-office.ml/wp-content/uploads/2020/04/スクリーンショット-2020-04-17-10.18.15.png?ssl=1" alt="" class="wp-image-3279" srcset="https://i0.wp.com/www.programmers-office.ml/wp-content/uploads/2020/04/スクリーンショット-2020-04-17-10.18.15.png?w=800&ssl=1 800w, https://i0.wp.com/www.programmers-office.ml/wp-content/uploads/2020/04/スクリーンショット-2020-04-17-10.18.15.png?resize=300%2C202&ssl=1 300w, https://i0.wp.com/www.programmers-office.ml/wp-content/uploads/2020/04/スクリーンショット-2020-04-17-10.18.15.png?resize=768%2C516&ssl=1 768w" sizes="(max-width: 800px) 100vw, 800px" data-recalc-dims="1" /> </figure> 

の割には終わり方があっさりしている・・・

### まとめ

実は下記コースの一部  
https://bitfumes.com/courses/vuejs/nuxtjs-for-everyone

そしてこれは、プレミアコース  
https://bitfumes.com/premium/nuxtjs-for-everyone  
$35なら悪くない気はします

ただ、やはり基礎ができていないことも感じる

Vueのフリーコースもある

<https://bitfumes.com/courses/vuejs/vuejs-beginner-series>

こちらは1時間でまとまっているというのが魅力  
Vue JS Crash Course<figure class="wp-block-embed-youtube wp-block-embed is-type-video is-provider-youtube wp-embed-aspect-16-9 wp-has-aspect-ratio">

<div class="wp-block-embed__wrapper">
  <span class="embed-youtube" style="text-align:center; display: block;"></span>
</div></figure> 

ただTypescriptバージョンで勉強したい<figure class="wp-block-embed-youtube wp-block-embed is-type-video is-provider-youtube wp-embed-aspect-16-9 wp-has-aspect-ratio">

<div class="wp-block-embed__wrapper">
  <span class="embed-youtube" style="text-align:center; display: block;"></span>
</div></figure> 

さらに遡ってVueの基本からやろう。