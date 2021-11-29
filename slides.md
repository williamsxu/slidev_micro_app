---
# try also 'default' to start simple
theme: seriph
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
# background: https://source.unsplash.com/collection/94734566/1920x1080
background: './img/conver.jpeg'
# apply any windi css classes to the current slide
class: 'text-center'
# https://sli.dev/custom/highlighters.html
highlighter: shiki
# some information about the slides, markdown enabled
download: true
layout: cover
fonts:
  sans: 'Helvetica Neue,Robot'
  local: 'Helvetica Neue'
  italic: true

info: |
  ## About
  ### 徐健
  ### 蜂泰科技--研发管理中心

---

<span class="text-teal-600 text-6xl ">如何瓦解巨石应用</span>

<span class="text-teal-300 text-2xl ">-- 微前端的实现思路及应用</span>


<div class="pt-12">
  <span class="text-teal-200 px-2 p-1">
  蜂泰科技  |  徐 健
  </span>
</div>


---
layout: 'intro'
---

# 徐 健

<div class="leading-8 opacity-80">
<div class="flex "><svg width="24" height="24" viewBox="0 0 48 48" fill="none" xmlns="http://www.w3.org/2000/svg"><rect width="48" height="48" fill="white" fill-opacity="0.01"/><path d="M48 0H0V48H48V0Z" fill="white" fill-opacity="0.01"/><path d="M41 18H19C18.4477 18 18 18.4477 18 19V41C18 41.5523 18.4477 42 19 42H41C41.5523 42 42 41.5523 42 41V19C42 18.4477 41.5523 18 41 18Z" fill="none" stroke="#333" stroke-width="4" stroke-linejoin="round"/><path d="M9.96906 6H6V10.0336" stroke="#333" stroke-width="4" stroke-linecap="round" stroke-linejoin="round"/><path d="M9.99705 30H6V26.012" stroke="#333" stroke-width="4" stroke-linecap="round" stroke-linejoin="round"/><path d="M26.0023 6H30V10.0152" stroke="#333" stroke-width="4" stroke-linecap="round" stroke-linejoin="round"/><path d="M16.0283 6H20.0083" stroke="#333" stroke-width="4" stroke-linecap="round" stroke-linejoin="round"/><path d="M6 16C6 18.6536 6 19.9869 6 20" stroke="#333" stroke-width="4" stroke-linecap="round" stroke-linejoin="round"/><path d="M30 16C30 18.6765 30 19.3456 30 18.0074" stroke="#333" stroke-width="4" stroke-linecap="round" stroke-linejoin="round"/><path d="M15.9927 30H18.0001" stroke="#333" stroke-width="4" stroke-linecap="round"/></svg>
<span class="mx-4">大前端工程师</span></div>
<div class='flex'><svg width="24" height="24" viewBox="0 0 48 48" fill="none" xmlns="http://www.w3.org/2000/svg"><rect width="48" height="48" fill="white" fill-opacity="0.01"/><path fill-rule="evenodd" clip-rule="evenodd" d="M11 14L25 4V44H11V14Z" fill="none" stroke="#333" stroke-width="4" stroke-linecap="round" stroke-linejoin="round"/><path d="M25 13L39 23V44" stroke="#333" stroke-width="4" stroke-linecap="round" stroke-linejoin="round"/><path d="M4 44H44" stroke="#333" stroke-width="4" stroke-linecap="round" stroke-linejoin="round"/></svg>
<span class="mx-4">研发管理中心架构组成员</span></div>
</div>


<img src="/img/avatar.jpeg" class="rounded-full w-40 abs-tr mt-45 mr-30"/>

---

# 目录

<br>
<br>
<br>
<br>

<div class="grid grid-cols-2 gap-x-4 mt-10"><div>

- ## 背景
- ## 解决方案对比
- ## 微前端优势
- ## 微前端核心设计理念
</div>

<div>

- ## 微前端技术选型
- ## 统一后台整体方案
- ## Q&A


</div></div>

---

# 背景
> 脱离实际使用场景的技术改造没有太大价值并且很难走远。


<div class="grid grid-cols-2 gap-x-4 mt-10"><div>

## 现状
<br>

* 技术债务：技术栈陈旧不堪，腐化速度越来越快；
* 耦合性高：多个业务团队同时维护一个巨石应用；
* 管理效率低：多个应用入口分散，权限分散；

</div>

<div>

## 痛点
<br>

* 开发、测试、部署、维护等环节繁琐，效率低；
* 改动成本高，出错率上升；
* 重复建设，造成资源浪费；
* 缺乏统一管理，使用成本上升；


</div></div>


---

# 解决方案对比
> 到了项目后期，怎么优化都不如进行项目拆分。

<div class="leading-6">

| 方案  | 描述  | 优点  | 缺点  |
|:---:|:---|:---|:---|
| <span class="title">Nginx路由转发</span>  |  通过Nginx配置反向代理来实现不同路径映射到不同应用  |  简单、快速   |   在切换应用时会触发浏览器刷新，影响体验，配置繁复  |
| <span class="title">iframe嵌套</span>   |  每个子应用嵌套一个iframe   |  实现简单，子应用之间天然隔离互不影响   |  iframe的样式显示、兼容性等都具有局限性   |
| <span class="title">Web Components</span>   |  采用纯Web Components技术编写组件   | 每个子应用拥有独立的script和css，可单独部署    |  对于历史系统改造成本高，子应用通信较为复杂易踩坑   |
| <span class="title">组合式应用路由分发</span>   |  每个子应用独立构建和部署，运行时由父应用来进行路由管理，应用加载，启动，卸载，以及通信   |  体验良好，可无感知切换，子应用相互隔离   |  需要解决样式冲突、变量对象污染、通信机制等技术点   |

</div>

<style>
  .title{
    @apply text-fuchsia-700;
  }
</style>

---

# 微前端方案优势
> 微前端是一种多个团队通过独立发布功能的方式来共同构建现代化 web 应用的技术手段及方法策略。-- Michael Geers 

<br>

<div class="grid grid-cols-4 gap-x-4">
<div>
<div class="title">

* **技术解耦**
</div>
<br>
<div class="content"><GoodTag class="mr-2"/>主框架不限制接入应用的技术栈，技术灵活；</div>
</div>

<div>
<div class="title">

* **独立开发、部署**
</div>
<br>
<span class="content"><GoodTag class="mr-2"/>微应用仓库独立，前后端可独立开发；</span><br>
</div>

<div>
<div class="title">

* **增量升级**
</div>
<br>
<span class="content"><GoodTag class="mr-2"/>复杂场景时，非常容易实施渐进式重构的手段和策略；</span>
</div>

<div>
<div class="title">

* **独立运行时**
</div>
<br>
<span class="content"><GoodTag class="mr-2"/>每个微应用之间状态隔离，运行时状态不共享;</span>
</div>

</div>

<img src="/img/micro_app.png" class="cotainer m-auto"/>


<style>
  .title{
    @apply my-1 mx-5 text-red-700;
  }
  .content{
    @apply leading-6;
  }
</style>

---
layout: two-cols
---

# 微前端核心设计理念
> 微前端是一种类似微服务的架构，将微服务的理念应用到前端。

<br>

<span class="title">

* 中心化路由-注册中心

</span>

<p class="content">
注册中心：服务提供方要注册通告服务地址，服务的调用方要能发现目标服务。

这点和 后端的微服务类似。

我们需要在一个地方，统一维护路由和服务的对应关系。
</p>

::right::

<div class="mt-10">
<span class="title">

* 分配一个路由给子应用：

</span>

```js
// router.js
import Vue from 'vue'
import VueRouter from 'vue-router'
import MyPage from './my-page.vue'

Vue.use(VueRouter)

const routes = [
  {
    path: '/my-page/*',
    name: 'my-page',
    component: MyPage,
  },
]

export default routes
```
</div>


<style>
  .title{
    @apply my-1 mx-5 text-red-700;
  }
  .content{
    @apply leading-6;
  }
</style>

---
layout: two-cols
---

# 微前端核心设计理念
> 基座统一管理生命周期，触发相应的生命周期事件。

<br>

<span class="title">

* 生命周期管理

</span>

<p class="content">
微前端的中心服务称为：基座。

基座需要控制服务的加载，卸载。这时候对于子服务而言，就涉及到子服务的应用的生命周期。

一般需要包括以下功能：
* 资源加载、渲染
* 子应用挂载、卸载
* 全局监听、事件更新

</p>

::right::

<div class="mt-10">
<span class="title">

* **qiankun** 框架的生命周期管理：

</span>

```js
// main.js
/**
 * bootstrap只会在微应用初始化时调用一次。通常做一些全局变量初始化。
 */
export async function bootstrap() {}

/**
 * 应用每次进入都会调用mount方法，通常会触发应用的渲染方法。
 */
export async function mount(props) {}

/**
 * 应用每次切出/卸载会调用的方法，通常会卸载微应用的应用实例。
 */
export async function unmount(props) {}

/**
 * 可选生命周期钩子，仅使用 loadMicroApp 方式加载微应用时生效。
 */
export async function update(props) {}
```
</div>


<style>
  .title{
    @apply my-1 mx-5 text-red-700;
  }
  .content{
    @apply leading-6;
  }
</style>

---
layout: two-cols
---

# 微前端核心设计理念
> JS沙箱和样式隔离，确保子应用样式、全局变量、事件等不干扰。

<br>

<span class="title">

* JS沙箱和样式隔离

</span>

<p class="content">

<GoodTag class="mr-2"/> JS沙箱通过Proxy代理子应用的全局对象，防止应用之间全局变量的冲突，记录或清空子应用的全局副作用函数，也可以向子应用注入全局变量用于定制化处理。

<GoodTag class="mr-2"/> 样式隔离是指对子应用的link和style元素的css内容进行格式化处理，确保子应用的样式只作用域自身，无法影响外部。

</p>

::right::

<div class="mt-10">
<span class="title">

* **micro app** 应用隔离：

</span>

<img src="/img/micro_app_div.png" class="cotainer m-auto"/>

<img src="/img/micro_app_subapp.png" class="cotainer m-auto"/>

</div>


<style>
  .title{
    @apply my-1 mx-5 text-red-700;
  }
  .content{
    @apply leading-6;
  }
</style>


---

# 微前端技术选型

<img src="/img/micro_app_compare.png" class="cotainer m-auto"/>

---

# 统一后台整体方案

<img src="/img/union_app_view.png" class="cotainer m-auto"/>

---
layout: center
class: text-center
---

# FAQ

---
layout: center
class: text-center
---

## 感谢聆听 !

# 💪 创造更高质量的应用
### 蜂泰科技 ｜ 徐健

<style>
h1,h2 {
  background: linear-gradient(
141.27deg
,#ff904e -4.24%,#ff5982 21.25%,#ec68f4 44.33%,#79e2ff 83.46%);
background-size: 200%;
-webkit-background-clip: text;
background-clip: text;
-webkit-animation: gradient-data-v-fb6d3afe 10s ease infinite;
animation: gradient-data-v-fb6d3afe 10s ease infinite;
-webkit-text-fill-color: transparent;
}
</style>

<!--
xxxx
-->

---
layout: center
class: text-center
---


## 本次演示所用的代码基于：[https://sli.dev](https://sli.dev)

<style>
h1,h2 {
  background: linear-gradient(
141.27deg
,#ff904e -4.24%,#ff5982 21.25%,#ec68f4 44.33%,#79e2ff 83.46%);
background-size: 200%;
-webkit-background-clip: text;
background-clip: text;
-webkit-animation: gradient-data-v-fb6d3afe 10s ease infinite;
animation: gradient-data-v-fb6d3afe 10s ease infinite;
-webkit-text-fill-color: transparent;
}
</style>