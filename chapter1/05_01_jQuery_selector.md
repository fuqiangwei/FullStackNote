---
Author: fuqiangwei
Date:   2015-12-22 19:26:36
Last Modified by:   fuqiangwei
Last Modified time: 2015-12-23 13:20:01
---

### 如何使用jQuery？

1. 加载JQuery库

一般网站用CDN加速，如果CDN加速失败，则请求本地加载，常见写法如下。另外如果需要支持IE 6/7/8，就使用jQuery 1.x版，否则使用最新版。

```html
<script type="text/javascript"
  src="//apps.bdimg.com/libs/jquery/1.11.3/jquery.min.js">
</script>
<script>
window.jQuery ||
  document.write(
    '<script src="js/jquery-1.11.3.min.js" type="text/javascript"><\/script>'
  );
</script>
```
2. 入口函数

```javascript
$(document).ready(function() {
  //代码
});

$(function () {
  //代码
})

```
|  两种写法都要记住，用哪个都可以，两种写法作用完全一样。

### 上述两种写法跟window.onload 有什么区别？

1. `window.onload` 只能写一次。如果写多次，只有最后一次生效。`jQuery`可以写多次均生效。
2. `window.onload`需等到所有的外部资源加载完毕之后才执行里面在函数。而`jQuery`是在DOM加载完毕之后就立即执行，性能较好。`无需等待图片或视频等资源加载完毕`。

| Note: 在使用jQuery在过程中  `$` `===` `jQuery`.

### jQuery选择器

jQuery选择器非常强大，主要分为四大类

- 基本选择器
- 层次选择器
- 过滤选择器
    - 基本过滤
    - 内容过滤
    - 可见性过滤
    - 属性过滤
    - 子元素过滤
    - 表单对象过滤
- 表单选择器

1. 基本选择器
