---
Author: fuqiangwei
Date:   2015-12-22 20:40:21
Last Modified by:   fuqiangwei
Last Modified time: 2015-12-22 20:40:21
---

DOM对象和jQuery对象的相互转换
get() : 就是把JQ转成原生JS
选择器

基本
*
.class
element
#id
selector1, selectorN, ...
层级
parent > child
ancestor descendant
prev + next
prev ~ siblings
基本筛选
:animated
:eq()
:even
:first
:gt()
:header
:lang()
:last
:lt()
:not()
:odd
:root
:target
内容筛选
:contains()
:empty
:has()
:parent

可见性筛选
:hidden
:visible
属性
[name|="value"]
[name*="value"]
[name~="value"]
[name$="value"]
[name="value"]
[name!="value"
[name^="value"]
[name]
[name="value"][name2="value2"]
子元素筛选
:first-child
:first-of-type
:last-child
:last-of-type
:nth-child()
:nth-last-child()
:nth-last-of-type()
:nth-of-type()
:only-child
:only-of-type()

表单
:button
:checkbox
:checked
:disabled
:enabled
:focus
:file
:image
:input
:password
:radio
:reset
:selected
:submit
:text

## index()

```html
<div>
    <h3>h0</h3>
    <h2>h1</h2>
    <h3>h1</h3>
    <h3 id="index">h3</h3>
    <h2>h4</h2>
    <h2>h5</h2>
</div>
```

```javascript
// index() 索引就是当前元素在所有兄弟节点中的位置
  console.log($('#index').index());  //3
```

$()下的常用方法
addClass()   removeClass()
width()   innerWidth()   outerWidth()
insertBefore()  before()
insertAfter()   after()
appendTo()   append()
prependTo()   prepend()
remove() detach()
on()  off()
scrollTop()

ev  pageX  which
preventDefault  stopPropagation
one()
offset()  position()
offsetParent()
val()
size()
each()

hover()
show()  hide()
fadeIn()   fadeOut()
fadeTo()
slideDown()   slideUp()


### remove() detach()  区别

1. 删除节点及节点行为
2. detach() : 跟remove方法一样，只不过会保留删除这个元素的操作行为



### width()   innerWidth()   outerWidth()

```javascript
$('div').width()  //width

$('div').innerWidth() //width + padding

$('div').outerWidth() //width + padding + border
//jQuery中的 outerWidth()   可以获取到隐藏元素的值
// 原生的JS中  offsetWidth : 获取不到隐藏元素的值
$('div').outerWidth(true) //width + padding + border + margin
```

### insertBefore()  before()
    insertAfter()   after()
    appendTo()   append()
    prependTo()   prepend()

```javascript
  //区别 ：后续操作变了
  $('span').insertBefore( $('div') ).css('background','red');

  $('div').before( $('span') ).css('background','red');
```

### ev  pageX  which

```javascript

// ev : event对象

ev.pageX(相对于文档的) : clientX(相对于可视区)

// ev.which : keyCode

ev.preventDefault();  //阻止默认事件

ev.stopPropagation();  //阻止冒泡的操作

return false;   //阻止默认事件 + 阻止冒泡的操作
```

### offset()  position()

```javascript
$('#div2').offset().left //获取到屏幕的左距离

$('#div2').position().left //到有定位的父级的left值,把当前元素转化成类似定位的形式
```

### offsetParent()

```javascript
  parent() //: 获取父级
  offsetParent() //: 获取有定位的父级
  parents() : 获取当前元素的所有祖先节点，参数就是筛选功能
  closest() : 获取最近的指定的祖先节点(包括当前元素自身),必须要写筛选的参数,只能找到一个元素
```

### size()  each()

```javascript
$('input').val();  //取值
$('input').val(456);  // 赋值
$('li').size(); //4 像length

  $('li').each(function(i,elem){   //一参：下标 二参 : 每个DOM元素

    $(elem).html(i);

  });
```

### 拖拽事件

```javascript
  var disX = 0;
  var disY = 0;

  $('div').mousedown(function(ev){

    disX = ev.pageX - $(this).offset().left;
    disY = ev.pageY - $(this).offset().top;

    $(document).mousemove(function(ev){

      $('div').css('left',ev.pageX - disX);
      $('div').css('top',ev.pageY - disY);

    });

    $(document).mouseup(function(){

      $(document).off();

    });

    return false;

  });
```

### hover() hide() show()

```javascript
hover() 等于 mouseenter  + mouseleave

hide(param)    param参数指毫秒  或者 fast(200)  normal(400) slow(600)
show()  slideUp()   slideDown()  同上

fadeTo("毫秒","opacity")
```

```javascript
  parent() //: 获取父级
  offsetParent() //: 获取有定位的父级
```
- 基础方法扩充
    + get()  :   下标和length属性
    + outerWidth()  :   针对隐藏元素和参数true
    + text()   :   合体的特例
    + remove()  :  detach()
    + $()   :  $(document).ready()

$()下的常用方法
parents()   closest()
siblings()
nextAll()  prevAll()
parentsUntil()   nextUntil()   prevUntil()
clone()
wrap()  wrapAll()  wrapInner()  unwrap()
add()  slice()
serialize()    serializeArray()
animate()
stop()
delay()
delegate()   undelegate()
trigger()
event.data    event.target   event.type


$('div').text() // 会获取所有的内容(特例)
$('div').html() //


### siblings()

siblings() : 找所有的兄弟节点，参数也是筛选功能
nextAll() : 下面所有的兄弟节点，参数也是筛选功能
prevAll() : 上面所有的兄弟节点
Until("h2") : 截止到h2,不包括h2    // parentsUntil()   nextUntil()   prevUntil()

### clone()

clone() : 可以接收一个参数(true) ，作用可以复制之前的操作行为

### wrap()  wrapAll()  wrapInner()  unwrap()

wrap() : 包装

wrapAll() : 整体包装
wrapInner() : 内部包装
unwrap() : 删除包装 ( 删除父级 : 不包括body )

```javascript
$('li').slice(1,4).css('background','red');
```

### serialize()    serializeArray()

```javascript
$('form').serialize();
$('form').serializeArray();
```

### animate() stop() finish()  delay(1000)

```javascript
//第一个参数 : {} 运动的值和属性
//第二个参数 : 时间(运动快慢的)  默认 : 400
//第三个参数 : 运动形式 只有两种运动形式 ( 默认 : swing(慢快慢) linear(匀速) )
//第四个参数 :  回调函数
$("div").animate({width : 300 , height : 300} , 4000 , 'linear',function(){
      //callback
    }).;

$('div').click(function(){

  //$('#div1').stop();   //默认 : 只会阻止当前运动

  //$('#div1').stop(true); //阻止后续的运动

  //$('#div1').stop(true,true); //可以立即停止到指定的目标点

  $('#div1').finish();  //立即停止到所有指定的目标点

});

```

### event.data    event.target   event.type

```javascript
  $('#div1').on('click',{name:'hello'},function(e){
    alert(e.data.name); // hello
    alert( e.target ); //div1
    alert( e.type ); //click
});

```

### $下的方法

不仅可以给JQ用，也可以给原生JS用 : 叫做工具方法


type()
trim()
inArray()
proxy()
noConflict()
parseJSON()
makeArray()
ajax() :  json形式的配置参数
url    success
error   contentType
data     type
dataType    cache     timeout
抽象出来的方法
get()
post()
getJSON()
支持jsonp的形式：指定?callback=?
插件
$
$.extend
$.fn
$.fn.extend
继续深入的话，我们还应该掌握哪些？
$.Callbacks()    :   回调对象
deferred()  :  延迟对象
$.hodeReady()   :  持有和释放ready
$.dequeue()  :  执行队列
$.support  :   功能检测

### type()

```javascript
  var a = new Date();
  $.type() : 也是判断类型,不过其更强大，可以判断 js具体内置对象
  alert( typeof a );
  alert( $.type(a) );
});

$.trim(str);

```
### inArray()

```javascript
  inArray() : 类似于 indexOf
  var arr = ['a','b','c','d'];
  alert(  $.inArray('b',arr)  );

  proxy()  : 改变this指向的


```

### proxy()  : 改变this指向的

```javascript
  function show(n1,n2){
    alert(n1);
    alert(n2);
    alert(this);
  }
  //this指向show
  show();
  //this指向document
  $.proxy(show , document,3)(4);
  $.proxy(show , document,)(3,4);
  ////this指向window
  $(document).click( $.proxy(show,window,3,4)  );

```
 inArray() : 类似于 indexOf
不仅可以给JQ用，也可以给原生JS用 : 叫做工具方法
