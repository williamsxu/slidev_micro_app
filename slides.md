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

info: |
  ## About
  ### 徐健
  ### 蜂泰科技--研发管理中心

---

# JavaScript编码不完全指南

-- 怎样写出难以维护的JavaScript（jQuery）代码


<div class="pt-12">
  <span class="px-2 p-1">
  蜂泰科技  |  徐 健
  </span>
</div>

<!--
The last comment block of each slide will be treated as slide notes. It will be visible and editable in Presenter Mode along with the slide. [Read more in the docs](https://sli.dev/guide/syntax.html#notes)
-->

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

# 注意

<div class="inline-flex mt-45 ml-70">请注意这个标记：<Dog class="mr-1.5"/></div>

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent; 
  -moz-text-fill-color: transparent;
}
</style>
---

# 使用单引号

<div class="inline-flex"><Dog class="mr-1.5"/>尽量不要简化符号，双引号越多越好。</div>

<br>
<br>

<BadTag />

```js
$("div").html("<img src='1.jpg'>");
```

<br>
<GoodTag />

```js
$('div').html('<img src="1.jpg">');
```


<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent; 
  -moz-text-fill-color: transparent;
}
</style>
---

# 变量
> 变量命名

<br>
<div class="inline-flex"><Dog class="mr-1.5"/>jQuery对象不要用$变量表示，这样就可以无法明确变量含义了。</div>

<br>
<br>

<BadTag />

```js
const sidebar = $('.sidebar');
```
<br>
<GoodTag />

```js
const $sidebar = $('.sidebar');
```


<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent; 
  -moz-text-fill-color: transparent;
}
</style>
---

# 变量
> 缓存变量

<br>
<div class="inline-flex"><Dog class="mr-1.5"/>虽然DOM 遍历是昂贵的，但是现在计算资源过剩，无需将会重用的元素缓存。</div>

<br>
<br>
<BadTag />

```js
var $element = $('#element'),
    h = $element.height();
$element.css('height', h - 20);
```
<br>

<GoodTag />

```js
var h = $('#element').height();
$('#element').css('height', h - 20);
```

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent; 
  -moz-text-fill-color: transparent;
}
</style>
---

# 变量
> 全局变量

<br>
<div class="inline-flex"><Dog class="mr-1.5"/>jquery 与 javascript 一样，你的变量可以随便全局定义，这样可以随便在函数作用域外使用。</div>

<br>
<br>
<BadTag />

```js
$element = $('#element');
h = $element.height();
$element.css('height',h - 20);
```
<br>

<GoodTag />

```js
var $element = $('#element'),
    h = $element.height();
$element.css('height',h - 20);
```

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent; 
  -moz-text-fill-color: transparent;
}
</style>
---

# 操作
> 选择器

<br>
<div class="inline-flex"><Dog class="mr-1.5"/>ID选择器可用时无所谓用不用,虽然我们知道它在内部使用document.getElementById()。</div>

<br>
<br>
<div class="inline-flex"><Dog class="mr-1.5"/>当使用类/伪类选择器时，上手就是直接写类名，给选择器附上元素类型来避免扫描整个DOM树不存在。</div>
<br>
<br>
<BadTag />

```js
// 在整个DOM树中扫描"products"类名
var $products = $(".products");
```
<br>

<GoodTag />

```js
// 只在DIV元素中扫描"products"类名
var $products = $("div.products");
```

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent; 
  -moz-text-fill-color: transparent;
}
</style>
---

# 操作
> 选择器

<br>
<div class="inline-flex"><Dog class="mr-1.5"/>在ID > 子节点层级选择器中使用find()方法无所谓的。前半部分选择器没使用到Sizzle选择器引擎来查找元素也没太多影响。</div>

<br>
<br>
<BadTag />

```js
// Sizzle选择器引擎查找层级
var $productIds = $("#products div.id");
```
<br>

<GoodTag />

```js
// 只有div.id走Sizzle选择器引擎
var $productIds = $("#products").find("div.id");
```

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent; 
  -moz-text-fill-color: transparent;
}
</style>
---

# 操作
> 选择器

<br>
<div class="inline-flex"><Dog class="mr-1.5"/>层级再多也不怕，总有能扫描到的时候。</div>

<br>
<br>
<BadTag />

```js
// 要扫描整个DOM树寻找
$('.class');
```
<br>

<GoodTag />

```js
// 只在#class-container里扫描
$('.class', '#class-container');
```

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent; 
  -moz-text-fill-color: transparent;
}
</style>
---

# 操作
> 使用 on 来处理事件

<br>
<div class="inline-flex"><Dog class="mr-1.5"/>自从 jquery 1.7 版本后，on() 是附加事件处理程序的首选方法。不必为了一致性考虑统一调用风格。</div>

<br>
<br>
<BadTag />

```js
$first.click(function(){
    $first.css('border', '1px solid red');
    $first.css('color', 'blue');
});
$first.hover(function(){
    $first.css('border', '1px solid red');
});
```
<br>

<GoodTag />

```js
$first.on('click', function(){
    $first.css('border', '1px solid red');
    $first.css('color', 'blue');
});
$first.on('hover', function(){
    $first.css('border', '1px solid red');
});
```

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent; 
  -moz-text-fill-color: transparent;
}
</style>
---

# 操作
> 行内JS

<br>
<div class="inline-flex"><Dog class="mr-1.5"/>可以为了方便在HTML文件里添加行为（行内JS），虽然这是调试的噩梦, 而且始终使用jQuery绑定事件后面会很容易去解绑事件。</div>

<br>
<br>
<BadTag />

```js
<a id="myLink" href="#" onclick="myEventHandler();">my link</a>
```
<br>

<GoodTag />

```js
$("#myLink").on("click", myEventHandler); 
```

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent; 
  -moz-text-fill-color: transparent;
}
</style>
---

# 操作
> 对事件使用自定义命名空间

<br>
<div class="inline-flex"><Dog class="mr-1.5"/>事件名称写得一摸一样，可以增加复制粘贴的速度。虽然自定义命名空间有利于去解绑某DOM元素上特定的事件而不会影响到该DOM元素上的其他事件。</div>

<br>
<br>

<GoodTag />

```js
$("#myLink").on("click.mySpecialClick", myEventHandler); // GOOD
// 后面会很容易的解绑这个特定的点击事件
$("#myLink").unbind("click.mySpecialClick");
```

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent; 
  -moz-text-fill-color: transparent;
}
</style>
---

# 操作
> 精简 jquery

<br>
<div class="inline-flex"><Dog class="mr-1.5"/>一般来说，最好尽可能合并属性。但不合并毕竟这样会显得代码很多不是么。</div>

<br>
<br>
<BadTag />

```js
$first.click(function(){
    $first.css('border', '1px solid red');
    $first.css('color', 'blue');
});
```
<br>

<GoodTag />

```js
$first.on('click', function(){
    $first.css({
        'border':'1px solid red',
        'color':'blue'
    });
});
```

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent; 
  -moz-text-fill-color: transparent;
}
</style>
---

# 操作
> 链式操作

<br>
<div class="inline-flex"><Dog class="mr-1.5"/>jQuery链式操作可能显得太简洁，毕竟还少写了不少代码。</div>

<br>
<br>
<BadTag />

```js
$second.html(value);
$second.on('click', function(){
    alert('hello everybody');
});
$second.fadeIn('slow');
$second.animate({height: '120px'}, 500);
```
<br>

<GoodTag />

```js
$second.html(value).on('click', function(){
    alert('hello everybody');
}).fadeIn('slow').animate({height: '120px'}, 500);
```

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent; 
  -moz-text-fill-color: transparent;
}
</style>

---

# Ajax

<div class="inline-flex"><Dog class="mr-1.5"/>不必避免使用.getJSON()和.get()，只使用$.ajax()。【前两者都是在内部使用的后者。】</div>
<br>
<br>
<div class="inline-flex"><Dog class="mr-1.5"/>直接把请求参数放在URL里，不用放在data对象里去。</div>
<br>
<br>
<BadTag />

```js
$.ajax({
    url: "something.com?param1=test1&param2=test2",
    ....
});
```
<br>

<GoodTag />

```js
$.ajax({
    url: "something.com",
    data: { param1: test1, param2: test2 }
});
```

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent; 
  -moz-text-fill-color: transparent;
}
</style>
---

# Ajax

<div class="inline-flex"><Dog class="mr-1.5"/>不必明确设置数据的类型dataType，虽然这样很容易知道当前正在处理什么样的数据。</div>
<br>
<br>

<GoodTag />

```js
var jqxhr = $.ajax({
  url: url,
  type: "GET",      // 默认值GET，可根据需要配置
  cache: true,      // 默认值true, dataType是'script'或'jsonp'时为false，可根据需要配置
  data: {},         // 请求参数对象
  dataType: "json", // 设置数据类型
  jsonp: "callback",// 只在操作JSONP时设置此项
  statusCode: {     // 针对特定错误码的回调处理函数
    404: handler404,
    500: handler500
  }
});
jqxhr.done(successHandler);
jqxhr.fail(failureHandler);
```

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent; 
  -moz-text-fill-color: transparent;
}
</style>
---

# 可读性
> 维持代码的可读性

<br>
<div class="inline-flex"><Dog class="mr-1.5"/>链式代码够精简了，要是不能读懂代码不关我事。</div>

<br>
<br>
<BadTag />

```js
$second.html(value).on('click', function(){
    alert('hello everybody');
}).fadeIn('slow').animate({height: '120px'}, 500);
```
<br>

<GoodTag />

```js
$second.html(value)
    .on('click', function() {
        alert('hello everybody');
    })
    .fadeIn('slow')
    .animate({
        height: '120px'
    }, 500);
```

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent; 
  -moz-text-fill-color: transparent;
}
</style>

---

# 更新

<br>
<div class="inline-flex"><Dog class="mr-1.5"/>现有版本能用就行，升不升级新版本无所谓。</div>

<br>
<br>
<div class="inline-flex"><Dog class="mr-1.5"/>不用关注每个新版本的废弃方法，又不是不能用。</div>
<br>
<br>
<BadTag />

```js
$('#stuff').on('click', function() {
    console.log('hooray');
});
```
<br>

<GoodTag />

```js
$second.html(value)
    .on('click', function() {
        alert('hello everybody');
    })
    .fadeIn('slow')
    .animate({
        height: '120px'
    }, 500);
```

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent; 
  -moz-text-fill-color: transparent;
}
</style>

---

# CDN

<div class="inline-flex mt-40"><Dog class="mr-1.5"/>虽然jQuery 官网提供了 CDN，但无需考虑利用它保证选择离用户最近的缓存并迅速响应。</div>

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent; 
  -moz-text-fill-color: transparent;
}
</style>

---

# 做个小结
> 来！该做个小结了！

<div grid="~ cols-2 gap-4">
  <div>
    <br>

* jQuery对操作DOM有一定的要求；

<br>

- 小结一下:
1. 选择节点范围能小则小；
2. 能重用资源越多越好；
3. 注意事件的解耦;

  </div>
  
  <div>
    <br>

* 现代框架对jQuery造成了冲击；

<br>

- 特点:
1. React 、Vue 、Angular框架，都是属于MV*框架的范畴，其设计特点，主要是以数据为核心；
2. 比传统jQuery开发效率高，代码可维护性高，可扩展性强、性能好；

</div>
<div>


</div>
</div>

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent; 
  -moz-text-fill-color: transparent;
}
</style>

---
layout: center
class: text-center
---

# 建造高质量的应用
## THANK YOU !

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