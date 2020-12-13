---
title: Realworld app – VueJS and Typescript
author: KONNO Kiyotaka
type: post
date: 2020-04-19T09:00:59+00:00
url: /realworld-app-vuejs-and-typescript/
featured_image: /wp-content/uploads/2018/11/imac-300x300.jpg
post_views_count:
  - 209
categories:
  - プログラミング
tags:
  - Vue

---
今度はTypescript<figure class="wp-block-embed-youtube wp-block-embed is-type-video is-provider-youtube wp-embed-aspect-16-9 wp-has-aspect-ratio">

<div class="wp-block-embed__wrapper">
  <span class="embed-youtube" style="text-align:center; display: block;"></span>
</div></figure> 

<https://github.com/gothinkster/realworld-starter-kit>

<hr class="wp-block-separator" />

### Part 1 : Introduction and Vue CLI Setup

<pre class="wp-block-code"><code>$ vue create realworld-vue-ts</code></pre>

[vue-class-component][1]

create component の代わりに@Component

[vue-property-decorator][2]

@Propなど

[vuex-module-decorators][3]

@module

<pre class="wp-block-code"><code>$ yarn serve</code></pre>

今回はyarn派なんですね

<pre class="wp-block-code"><code>$ yarn add vue-property-decorator
$ yarn add vuex-module-decorators</code></pre>

<hr class="wp-block-separator" />

### Part 2 : Templates and Styling

router.ts がなくなっていて、router/index.ts

VSCode command + D で複数選択

<hr class="wp-block-separator" />

### Part 3 : Vuex and API Access

<https://github.com/gothinkster/realworld/tree/master/api>

json to ts

<https://jvilk.com/MakeTypes/>

<pre class="wp-block-code"><code>$ yarn add axios</code></pre>

[axios npm][4]

JWT JSON Web Token

やべえ、何一つわからない

<pre class="wp-block-code"><code>export async function loginUser(user: UserSubmit): Promise&lt;UserResponse | undefined> {
    try {
        const response = await axios.post('/users/login', {
            user
        })
        return (response.data as UserResponse)
    } catch (e) {
        console.error(e)
    }
}</code></pre>

Promise<>  
| undefined  
as UserResponse  
console.error

MutationAction

<https://github.com/championswimmer/vuex-module-decorators>{.aioseop-link}

mutate　変異する  
自動的にmutateする 

vue.config.js

dynamic: true

Property &#8216;login&#8217; does not exist on type &#8216;VueConstructor&#8217;.  
import users from &#8216;@/store/modules/users.vue&#8217;;  
import users from &#8216;@/store/modules/users&#8217;;

baseURL  
を使えていない  
POST http://localhost:8080/users/login 404 (Not Found)  
いったん  
const response = await axios.post(&#8216;https://conduit.productionready.io/api/users/login&#8217;, {

Error: Request failed with status code 422  
at createError (createError.js?2d83:16)  
at settle (settle.js?467f:17)  
at XMLHttpRequest.handleLoad (xhr.js?b50d:61)

POSTMAN  
{  
&#8220;errors&#8221;: {  
&#8220;email or password&#8221;: [  
&#8220;is invalid&#8221;  
]  
}  
}

@Mutation  
@Action

もう少し進めてみる

・・・と思いましたが、もう少し初心者向けから出直してきます。

 [1]: https://github.com/vuejs/vue-class-component
 [2]: https://github.com/kaorun343/vue-property-decorator
 [3]: https://github.com/championswimmer/vuex-module-decorators
 [4]: https://www.npmjs.com/package/axios