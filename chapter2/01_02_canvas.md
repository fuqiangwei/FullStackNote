---
Author: fuqiangwei
Date:   2015-12-28 10:31:52
Last Modified by:   fuqiangwei
Last Modified time: 2016-01-15 15:08:31
---

# canvas

1. `canvas简介`
    + 什么是`canvas`
    + `canvas`的历史
    + `canvas`主要应用的领域
2. `Canvas`初识
    + `canvas`的初体验：
    + `canvas`标签语法和属性
    + 语法
    + 注意点
    + 浏览器不兼容的处理
3. `canvas`的应用
    + 基本方法：
    +` getContext（“2d/3d”）`
    + 基本的绘制路径
    + `canvas`坐标系
    + 设置绘制起点(moveTo)
    + 绘制直线(lineTo)
    + 路径开始和闭合
    + 描边(stroke)
    + 填充(fill)
    + 路径的一些属性：
    + 案例：表格绘制html
    + 绘制矩形（重点）
    + 快速创建矩形（rect）
    + 快速创建描边矩形和填充矩形（strokeRect、fillRect）
    + 清除矩形（clearRect）
    + 绘制圆形（arc）
    + 绘制文字（重点）
    + 上下文绘制文字方法
    + 绘制上下文的文字属性
    + 综合案例：
    + 案例：文字绘制html	0
    + 绘制图片（重点）
4. 面向对象基础复习补充
    + 创建对象：
    + 用json方式创建对象
    + 使用object的new方式创建对象
    + 使用构造函数来创建对象
    + js中this的学习（函数调用的四种模式）：
    + 函数执行模式
    + 对象方法的调用模式
    + 构造器的调用模式
    + 使用其它方法来改变this模式：（apply,call）
    + 案例：
5. `canvas`补充api
    + Canvas颜色样式
    + 设置阴影
    + 复杂样式
    + 创建线性渐变的样式
    + 设置圆形渐变（径向渐变）
    + 绘制背景图
    + 变换
    + 如果以后做canvas游戏方向开发深入学习可以扩展内以下容：
6. konva库的学习：
    + Konva的整体理念
---

## **canvas** 简介

#### What is `canvas` ?

+ ` canvas   /canvas `是HTML提供的一种新标签．（英 `['kænvəs]`  美 `['kænvəs] `  帆布 画布）

+ `Canvas`是一个矩形区域的画布，可以用JavaScript在上面绘画。控制其每一个像素。
+ `canvas` 标签使用 JavaScript 在网页上绘制图像，本身不具备绘图功能。
+ `canvas` 拥有多种绘制路径、矩形、圆形、字符以及添加图像的方法。

HTML之前的web页面只能用一些固定样式的标签：比如p、div、h等，但有了canvas Web页面可以可以丰富多彩。

#### canvas的历史

`Canvas`标签被很多的工程师认为是HTML最伟大的改进之一，因为它可以让我们在不使用图片的情况下实现网页的图形设计。
canvas 标记由 Apple 在 Safari  Web 浏览器中引入。对 HTML 的这一根本扩展的原因在于，HTML 在 Safari 中的绘图能力也为 Mac OS X 桌面的 Dashboard 组件所使用，并且 Apple 希望有一种方式在 Dashboard 中支持脚本化的图形。

Firefox和 Opera都跟随了 Safari 的引领。这两个浏览器都支持  canvas  标记。

我们甚至可以在 IE 中使用  canvas  标记，并在 IE 的 VML 支持的基础上用开源的 JavaScript 代码（由 Google 发起）来构建兼容性的画布。

canvas  的标准化的努力由一个 Web 浏览器厂商的非正式协会在推进，目前  canvas  已经成为 HTML  草案中一个正式的标签。

#### canvas主要应用的领域

+ 游戏：canvas在基于Web的图像显示方面比Flash更加立体、更加精巧，canvas游戏在流畅度和跨平台方面更牛逼的 HTML Canvas 游戏
+ 可视化数据数据图表话，比如:百度的echart
+ banner广告：Flash曾经辉煌的时代，智能手机还未曾出现。现在以及未来的智能机时代，HTML技术能够在banner广告上发挥巨大作用，用Canvas实现动态的广告效果再合适不过。
+ 其他可嵌入网站的内容(多用于活动页面、特效)：类似图表、音频、视频，还有许多元素能够更好地与Web融合，并且不需要任何插件。
完整的canvas移动化应用

##### 未来可能方向:
模拟器：无论从视觉效果还是核心功能方面来说，模拟器产品可以完全由JavaScript来实现。
远程计算机控制：Canvas可以让开发者更好地实现基于Web的数据传输，构建一个完美的可视化控制界面。
图形编辑器：Photoshop图形编辑器将能够00%基于Web实现。

canvas的标准：
[最新标准](http://wwwworg/TR/dcontext/)
[稳定版本的标准](http://wwwworg/TR/0/CR-dcontext-000/)
目前来说，标准还在完善中。先用早期的api足够完成所有的应用

## Canvas 初识

canvas 的初体验

```html
     <canvas id="mycanvas" width="400" height="300">
        您好，您的浏览器不支持canvas，请升级您的浏览器到最新版本。
     </canvas>
```

canvas 标签语法和属性
标签名canvas，需要进行闭合。就是一普通的html标签。
跟所有的html标签一样，要写在body标签之内。

Note：
+ `canvas` 元素本身是没有绘图能力的。所有的绘制工作必须通过JavaScript操控完成
+ `canvas`画布`width:300px` `height:150px`。不要用CSS去设置canvas画布的宽和高,如果用css设置了canvas的宽高，画布将会整体缩放.
+ 重新设置canvas标签的宽高属性会让画布擦除所有的内容.
+ 可以给canvas画布通过style属性设置其它属性（背景色， 边框。。。。）

一般主流浏览器都支持canvas,IE9以上才支持canvas.只要浏览器兼容canvas，那么就会支持绝大部分api(个别最新api除外).另外移动端的兼容情况非常理想，基本上都可以随便使用。2d的支持的都非常好，3d（webgl）ie11才支持，如果浏览器不兼容，最好进行友好提示

```html
     <canvas id="mycanvas">
        您好，您的浏览器不支持canvas，请升级您的浏览器到最新版本。
     </canvas>
```

## canvas 的应用

  基本方法：
    getContext（“2d”）
	得到canvas的上下文对象（是所有的绘制操作api的入口或者集合，相当于是得到画布的控制权，之后便可以通过js在画布上画内容了）
	后面的参数是字符串的“d”,d表示当前的画布支持D绘图，如果希望将当前画布支持d，则传入”webgl”（d在ie中只有ie才支持，d一般应用在D模型和场景，这里不讨论）
var canvas  = documentgetElementById('mycanvas'); //获得画布
var ctx = canvasgetContext( 'd' );//注意：d小写， d：webgl
  基本的绘制路径（重点）
   canvas坐标系
canvas坐标系，从最左上角0,0开始。x向右增大， y向下增大

   设置绘制起点(moveTo)
* 语法：ctxmoveTo(x, y);
* 解释：设置上下文绘制路径的起点。相当于移动画笔到某个位置
* 参数：x,y 都是相对于 canvas盒子的最左上角。
* 注意：**绘制线段前必须先设置起点，不然绘制无效。**
   绘制直线(lineTo)
* 语法：ctxlineTo(x, y);
* 解释：从x,y的位置绘制一条直线到起点或者上一个线头点。
* 参数：x,y 线头点坐标。
   路径开始和闭合
* 开始路径：ctxbeginPath();
* 闭合路径：ctxclosePath();
* 解释：如果复杂路径绘制，必须使用路径开始和结束。闭合路径会自动把最后的线头和开始的线头连在一起。
* beginPath: 核心的作用是将 不同绘制的形状进行隔离，
  每次执行此方法，表示重新绘制一个路径,跟之前的绘制的墨迹可以进行分开样式设置和管理。
   描边(stroke)
* 语法：ctxstroke();
* 解释：根据路径绘制线。路径只是草稿，真正绘制线必须执行stroke
* stroke: （用笔等）画；轻抚；轻挪；敲击；划尾桨；划掉；（打字时）击打键盘
 英 [strəʊk]   美 [strok]
   填充(fill)
* 语法：ctxfill();
* 解释：填充，是将闭合的路径的内容填充具体的颜色。默认黑色。
* 注意：交叉路径的填充问题，“非零环绕原则”，顺逆时针穿插次数决定是否填充。

    以下是非0环绕原则的原理：（了解即可，非常少会用到复杂的路径）
    “非零环绕规则”是这么来判断有自我交叉情况的路径的：对于路径中的任意给定区域，从该区域内部画一条足够长的线段，
    使此线段的终点完全落在路径范围之外。
    图-中的那三个箭头所描述的就是上面这个步骤。
    接下来，将计数器初始化为0，
    然后，每当这条线段与路径上的直线或曲线相交时，
    就改变计数器的值。如果是与路径的顺时针部分相交，则加，
    如果是与路径的逆时针部分相交，则减。若计数器的最终值不是0，那么此区域就在路径里面，在调用fill()方法时，
    浏览器就会对其进行填充。
    如果最终值是0，那么此区域就不在路径内部，浏览器也就不会对其进行填充了
* 案例： 0填充矩形html

   路径的一些属性：
	strokeStyle
设置路径的描边样式
	fillStyle
设置路径的填充样式
以上两个值都可以接受颜色名,进制数据，rgb值，甚至rgba一般先进行设置样式然后进行绘制。
 例如：
	    ctxstrokeStyle = "red";
	    ctxstrokeStyle = "#ccc";
	    ctxstrokeStyle = "rgb(,0,0)";
	    ctxstrokeStyle = "rgba(,0,0,)";
	lineWidth
设置路径的宽度

   案例：表格绘制html

  绘制矩形（重点）
   快速创建矩形（rect）
* 语法：ctxrect(x, y, width, height);
* 解释：x, y是矩形左上角坐标， width和height都是以像素计
* rect方法只是规划了矩形的路径，并没有填充和描边。
* 改造案例：0填充矩形html
*rect: abbr 矩形（rectangular）；收据（receipt）
   快速创建描边矩形和填充矩形（strokeRect、fillRect）
* 语法： ctxstrokeRect(x, y, width, height);
    - 参数跟相同，注意此方法绘制完路径后立即进行stroke绘制
* 语法：ctxfillRect(x, y, width, height);
    - 参数跟相同， 此方法执行完成后。立即对当前矩形进行fill填充。
   清除矩形（clearRect）
* 语法：ctxclearRect(x, y, width, hegiht);
* 解释：清除某个矩形内的绘制的内容，相当于橡皮擦。
  绘制圆形（arc）（重点）
•	概述：arc() 方法创建弧/曲线（用于创建圆或部分圆）。
o	语法：ctxarc(x,y,r,sAngle,eAngle,counterclockwise);
o	arc: 弧（度）弧形物；天穹 英 [ɑːk] 美 [ɑrk]
o	counter 反击，还击；反向移动，对着干；反驳，回答 ['kaʊntə] 美 ['kaʊntɚ]
o	解释：
	x,y：圆心坐标。
	r：半径大小。
	sAngle:绘制开始的角度。 圆心到最右边点是0度，顺时针方向弧度增大。
	eAngel:结束的角度，注意是弧度。π
	counterclockwise：是否是逆时针。true是逆时针，false：顺时针
	弧度和角度的转换公式： rad = deg*MathPI/0;
	在Math提供的方法中sin、cos等都使用的弧度

•	案例：0绘制圆形html
•	案例：0绘制饼状图html
  绘制文字（重点）
   上下文绘制文字方法（重点）
	在画布上绘制“被填充的”文本  （fillText）
* 语法：ctxfillText(text,x,y,maxwidth);
* 解释：text是输出的文本， x, y是矩形左上角坐标， maxWidth（可选）允许的最大文本宽度，以像素计
* fillText方法在画布上绘制填色的文本。文本的默认颜色是黑色。
效果图：

	在画布上绘制文本（strokeText）（无填充）
* 语法：ctxstrokeText(text,x,y,maxwidth);
* 解释：text是输出的文本， x, y是矩形左上角坐标， maxWidth（可选）允许的最大文本宽度，以像素计
* strokeText方法在画布上绘制文本（没有填色）。文本的默认颜色是黑色。
效果图：

	在画布上绘制文本（measureText）（无填充）
* 语法：ctxmeasureText(text)width;
* 解释：text是要得到宽度的文本
* measureText 方法返回包含一个对象，该对象包含以像素计的指定字体宽度
* 单词：measure 测量；估量；权衡   英 ['meʒə]   美 ['mɛʒɚ]
   绘制上下文的文字属性 （有印象就行了）
•	font 设置或返回文本内容的当前字体属性
o	font 属性使用的语法与 CSS font 属性相同。
例如：ctxfont = "px '微软雅黑'";
•	textAlign 设置或返回文本内容的当前对齐方式
o	start : 默认。文本在指定的位置开始。
o	end : 文本在指定的位置结束。
o	center: 文本的中心被放置在指定的位置。
o	left : 文本左对齐。
o	right : 文本右对齐。
    * 例如：ctxtextAlign = 'left';

•	textBaseline 设置或返回在绘制文本时使用的当前文本基线
o	alphabetic ： 默认。文本基线是普通的字母基线。
o	top ： 文本基线是 字符的顶端。。
o	hanging ： 文本基线是悬挂基线。
o	middle ： 文本基线是字符的正中。
o	ideographic： 文本基线是字符基线。
o	bottom ： 文本基线是字符的底端。
    例如： ctxtextBaseline = 'top';
    单词:
     alphabetic: 字母的；照字母次序的   [,ælfə'bɛtɪk]
     ideographic：表意的；表意字构成的   英 [,ɪdɪəʊ'ɡræfɪk]   美 [,ɪdɪə'græfɪk]



   综合案例：
    ctxmoveTo( 00, 00 );
    ctxfillStyle = "purple";               //设置填充颜色为紫色
    ctxfont = '0px "微软雅黑"';           //设置字体
    ctxtextBaseline = "bottom";            //设置字体底线对齐绘制基线
    ctxtextAlign = "left";                 //设置字体对齐的方式
    //ctxstrokeText( "left", 0, 00 );
    ctxfillText( "Top-g", 00, 00 );        //填充文字
	效果图：

    案例：文字绘制html

   绘制图片（重点）
	 基本绘制图片的方式
* 语法：contextdrawImage(img,x,y);
* 解释：x,y 绘制图片左上角的坐标， img是绘制图片的dom对象。
	在画布上绘制图像，并规定图像的宽度和高度
* 语法：contextdrawImage(img,x,y,width,height);
* 解释：width 绘制图片的宽度，  height：绘制图片的高度
* 如果指定宽高，最好成比例，不然图片会被拉伸 /em
    等比公式：  toH = Height * toW   /  Width;  //等比
             设置高 = 原高度 * 设置宽/ 原宽度;
	图片裁剪，并在画布上定位被剪切的部分
* 语法：contextdrawImage(img,sx,sy,swidth,sheight,x,y,width,height);
* 解释：
    sx,sy 裁剪的左上角坐标，
    swidth：裁剪图片的高度。 sheight:裁剪的高度
    其他同上
	用JavaScript创建img对象
第一种方式：
   var img = documentgetElementById("imgId");
第二种方式：
    var img = new Image();//这个就是 img标签的dom对象
    imgsrc = "imgs/arcgif";
    imgalt = "文本信息";
    imgonload = function() {
        //图片加载完成后，执行此方法
    }

四、 面向对象基础复习补充：（了解）
**************
**************
  创建对象：
   用json方式创建对象
    * var o = { name: '', age: , sayHi: function(){alert(thisname);} };
   使用object的new方式创建对象
    * var o = new Object();  //通过new的方式创建
   使用构造函数来创建对象
    * var o = new Persion(); //通过类的构造函数创建
	构造函数的声明：
    * function Person (){
    		thisname = "zhangsan";
		thisage = "";
		thissayHi = function(){
			alert(“Hi”);
		};
		thissayName = function(){
			alert(thisname);
		}
	}
	属性的值从外部传入
function Person(name,age){
	thisname = name;
	thisage = age;
	thissayHi = function(){
		alert(thisname);
	}
	thissayName = function(){
		alert(thisname);
	}
}

	将方法封装到原型中
function Person (name,age){
	thisname =name;
	thisage = age;
}
PersonprototypesayHi = function(){
	alert(“Hi”);
｝
PersonprototypesayName = function(){
	alert(thisname);
｝

	将所有的方法统一次性管理到原型对象中：
function Person (name,age){
	thisname = name;
	thisage = age;
}
Personprototype = {
	sayHi: function(){
		alert(thisname);
	},
	sayHa:function(){
		alert("haha");
	}
}
	将对象属性的初始化也放到原型中（最终形态）：
function Person(option){
	this_init(option);
}
Personprototype = {
	_init: function(option){
	thisname = optionname;
	thisage = optionage;
	},
	sayHi: function(){
		alert(thisname);
	},
	sayHa:function(){
		alert("haha");
	}
     }
        * 直接添加属性：var o = {};  oage = ;//太分散了，不利于管理
    * 由于js动态语言的特性，如果属性不存在的时候，直接添加属性。
    * 构造函数添加属性
    * 原型添加公共的属性
JS的构造函数的原型 构造函数的原型就是：构造对象的模板，构造函数原型里面的所有的属性和方法都会共享给所有的 构造函数构造出来的所有。实。
  js中this的学习（函数调用的四种模式）：
this调用对象地址的引用（谁调用this就是谁）。
   函数执行模式
function add( a, b) {
		consolelog( this );
		return a+b;
}
add();// this === window //true
在这种模式中，方法相当是在window下定义的，所以在调用的时候时候相当于是调用windowadd();所有在add中的this是window
   对象方法的调用模式
function Cat() {
	thisshow = function() {
	    consolelog(this);// this === c;
	};
}
var c = new Cat();
cshow(); // 对象调用自己的方法，
在这种模式中，由于用到new，所以c相当于是创建出来对象的地址的引用。所以这里的this就是c
   构造器的调用模式
function Cat() {
	consolelog(this);
}
Catprototypeshow = function(){
	consolelog(this);
}
var c = new Cat();
cshow();// 构造器调用模式： this 指向 构造出来的对象。
   使用其它方法来改变this模式：（apply,call）(知道即可)
  案例：
将帧动画以面向对象方式完成

五、  canvas 补充api(其它方法)：
  Canvas颜色样式
	fillStyle  : 设置或返回用于填充绘画的颜色
	strokeStyle  : 设置或返回用于笔触的颜色
以上两个值都可以接受颜色名,进制数据，rgb值，甚至rgba一般先进行设置样式然后进行绘制。
 例如：
	    ctxstrokeStyle = "red";
	    ctxstrokeStyle = "#ccc";
	    ctxstrokeStyle = "rgb(,0,0)";
	    ctxstrokeStyle = "rgba(,0,0,)";
   设置阴影（了解，少用，性能差）
	shadowColor  ：   设置或返回用于阴影的颜色
	shadowBlur   ：   设置或返回用于阴影的模糊级别,大于的正整数，数值越高，模糊程度越大
	shadowOffsetX：   设置或返回阴影距形状的水平距离
	shadowOffsetY：   设置或返回阴影距形状的垂直距离
示例代码：
    ctxfillStyle = "rgba(,0,0, )"
    ctxshadowColor = "teal";
    ctxshadowBlur = 0;
    ctxshadowOffsetX = 0;
    ctxshadowOffsetY = 0;
    ctxfillRect(00, 00, 00, 00);
  复杂样式（了解）
   创建线性渐变的样式（了解）
 注意点：
	一般不用，都是用图片代替，canvas绘制图片效率更高。
	线性渐变可以用于 矩形、圆形、文字等颜色样式
	线性渐变是一个对象
	ctxcreateLinearGradient(x0,y0,x,y);
	x0:起点的横坐标
	y0:起点的纵坐标
	x:结束点的横坐标
	y:结束点的纵坐标
示例：
 //创建线性渐变的对象，
    var grd=ctxcreateLinearGradient(0,0,0,0);
    grdaddColorStop(0,"black");  //添加一个渐变颜色，第一个参数介于 00 与 0 之间的值，表示渐变中开始与结束之间的位置。
    grdaddColorStop(,"white");  //添加一个渐变颜色
    ctxfillStyle =grd;           //关键点，把渐变设置到 填充的样式
   设置圆形渐变（径向渐变）（了解）
	创建放射状/圆形渐变对象。可以填充文本、形状等
	语法：contextcreateRadialGradient(x0,y0,r0,x,y,r);
	x0:渐变的开始圆的横坐标
	y0:渐变的开始圆的纵坐标
	r0:渐变的开始圆的半径
	x0:渐变的结束圆的横坐标
	y0:渐变的结束圆的纵坐标
	r0:渐变的结束圆形的半径
	radial   半径的；放射状的；光线状的   英 ['reɪdɪəl]   美 ['redɪəl]
   绘制背景图（了解）
	ctxcreatePattern(img,repeat) 方法在指定的方向内重复指定的元素
	image ：规定要使用的图片、画布或视频元素。
	repeat ： 默认。该模式在水平和垂直方向重复。
   其它值 ：
 repeat   ：   默认。该模式在水平和垂直方向重复。
 repeat-x ：   该模式只在水平方向重复。
 repeat-y ：   该模式只在垂直方向重复。
 no-repeat：   该模式只显示一次（不重复）。
	pattern：n 模式；图案；样品  英 ['pæt(ə)n]   美 ['pætɚn]
   变换（重点）
	缩放（重点）
	scale() 方法缩放当前绘图，更大或更小
	语法：contextscale(scalewidth,scaleheight)
	scalewidth  :  缩放当前绘图的宽度 (=00%, 0=0%, =00%, 依次类推)
	scaleheight :  缩放当前绘图的高度 (=00%, 0=0%, =00%, etc)
	注意：缩放的是整个画布，缩放后，继续绘制的图形会被放大或缩小。
	位移画布（重点）
	translate() 方法重新映射画布上的 (0,0) 位置
	语法：contexttranslate(x,y)
	 x：   添加到水平坐标（x）上的值
	 y：   添加到垂直坐标（y）上的值
	注意：发生位移后，相当于把画布的0,0坐标 更换到新的x,y的位置，所有绘制的新元素都被影响。
	旋转（重点）
	rotate() 方法旋转当前的绘图
	语法：contextrotate(angle)
	 angle：   参数是弧度（PI）
注意：如需将角度转换为弧度，请使用 degrees*MathPI/0 公式进行计算。
	绘制环境保存和还原（重要）
	contextsave() 保存当前环境的状态（可以把当前绘制环境进行保存到缓存中）
	contextrestore() 返回之前保存过的路径状态和属性(获取最近缓存的ctx)
注意：一般配合位移画布使用。
	设置绘制环境的透明度（了解）
	contextglobalAlpha=number;
	number:透明值。必须介于 00（完全透明)与 0（不透明） 之间。
注意：设置透明度是全局的透明度的样式。注意是全局的。
	画布限定区域绘制（了解）
	clip() 方法从原始画布中剪切任意形状和尺寸
	语法：contextclip()
	 没有参数
注意：
 一旦剪切了某个区域，则所有之后的绘图都会被限制在被剪切的区域内（不能访问画布上的其他区域）。
 一般配合绘制环境的保存和还原。

位移画布一般配合缩放和旋转等

	画布保存base编码内容（重要）
	toDataURL() 把canvas绘制的内容输出成base内容。
	语法：canvastoDataURL(type, encoderOptions);
	 type：   设置输出的类型，比如 image/png   image/jpeg等
	encoderOptions： 0-之间的数字，用于标识输出图片的质量，表示无损压缩，类型为： image/jpeg 或者image/webp才起作用。
代码：
var canvas = documentgetElementById("canvas");
var dataURL = canvastoDataURL();
consolelog(dataURL);
// "data:image/png;base,iVBORw0KGgoAAAANSUhEUgAAAAUAAAAFCAYAAACNby
    // blAAAADElEQVQImWNgoBMAAABpAAFEIARAAAAAElFTkSuQmCC"
var img = documentquerySelector("#img-demo");//拿到图片的dom对象
imgsrc = canvastoDataURL("image/png");
	画布渲染画布（重要）
	drawImage() 在一个画布上画
	语法：contextdrawImage(img,x,y)
	 img ：也可以是画布，也就是把一个画布整体的渲染到另外一个画布上。
代码：
 var canvas = documentquerySelector('#cavsElem');
 var canvas = documentquerySelector('#cavsElem');
 var ctx = canvasgetContext('d');
 var ctx = canvasgetContext('d');
 ctxfillRect(0, 0, 0, 0);      //在第一个画布上绘制矩形
 ctxdrawImage(canvas, 0, 0);    //将第一个画布整体绘制到第二个画布上
	了解：线条样式（了解）
	lineCap	：设置或返回线条的结束端点(线头、线冒)样式
	  butt  ：  默认。向线条的每个末端添加平直的边缘。
 butt -  翻译：屁股；烟头；笑柄；靶垛；  英 [bʌt]   美 [bʌt]
	  round ：  向线条的每个末端添加圆形线帽。
	  square：  向线条的每个末端添加正方形线帽。
	lineJoin 	：设置或返回两条线相交时，所创建的拐角类型
	bevel:   创建斜角。
 bevel  - 翻译 斜角；斜面  英 ['bev(ə)l]  美 ['bɛvl]
	round:   创建圆角。
	miter:   默认。创建尖角
	lineWidth   设置或返回当前的线条宽度
	miterLimit	  设置或返回最大斜接长度
 意思:  斜接 英 ['maɪtə]
 斜接长度指的是在两条线交汇处内角和外角之间的距离。
 一般用默认值：0就可以了。除非需要特别长的尖角时，使用此属性。
0	了解贝塞尔曲线（知道有）
绘制一条二次贝塞尔曲线:
	quadraticCurveTo()二次贝塞尔曲线
	quadratic：二次方的意思， 英 [kwɒ'drætɪk]   美 [kwɑ'drætɪk]
	Curve：曲线的意思， 英 [kɜːv]   美 [kɝv]
	语法： contextquadraticCurveTo(cpx,cpy,x,y);
参数：
     cpx：   贝塞尔控制点的 x 坐标
     cpy：   贝塞尔控制点的 y 坐标
     x  ：   结束点的 x 坐标
     y  ：   结束点的 y 坐标
    ctxbeginPath();
    ctxmoveTo(0,0);
    //绘制次方曲线，贝赛尔曲线
    ctxquadraticCurveTo(0,00,00,0);
    ctxstroke();
绘制一条三次贝塞尔曲线
	bezierCurveTo():绘制一条三次贝塞尔曲线
	语法： contextquadraticCurveTo(cpx,cpy,x,y);
参数：
     cpx：    第一个贝塞尔控制点的 x 坐标
     cpy：    第一个贝塞尔控制点的 y 坐标
     cpx：    第二个贝塞尔控制点的 x 坐标
     cpy：    第二个贝塞尔控制点的 y 坐标
     x  ：   结束点的 x 坐标
     y  ：   结束点的 y 坐标
//绘制复杂的贝塞尔曲线
ctxbeginPath();
ctxmoveTo(00,00);
//参数说明：contextbezierCurveTo(cpx,cpy,cpx,cpy,x,y);
// cpx： 第一个贝塞尔控制点的 x 坐标
// cpy： 第一个贝塞尔控制点的 y 坐标
// cpx： 第二个贝塞尔控制点的 x 坐标
// cpy： 第二个贝塞尔控制点的 y 坐标
// x: 结束点的 x 坐标
// y: 结束点的 y 坐标
ctxbezierCurveTo(00, 00, 00, 00, 00, 00);
ctxstroke();
	了解创建两条切线的弧（知道有）
	arcTo在画布上创建介于当前起点和两个点形成的夹角的切线之间的弧
	quadratic：二次方的意思， 英 [kwɒ'drætɪk]   美 [kwɑ'drætɪk]
	Curve：曲线的意思， 英 [kɜːv]   美 [kɝv]
	语法： contextarcTo(x,y,x,y,r); //类比：css中的圆角。
参数：
      x:  弧的端点的 x 坐标
      y:  弧的端点的 y 坐标
      x:  弧的端点(终点)的 x 坐标
      y:  弧的端点(终点)的 y 坐标
      r :  弧的半径
代码：
    ctxbeginPath();
    ctxmoveTo(0,0);
ctxbeginPath();
ctxmoveTo(00,00);
ctxlineTo(00,00);
//contextarcTo(x,y,x,y,r); //类比：css中的圆角。
ctxarcTo(0, 00, 0, 0, 0);
ctxlineTo(0, 00);
ctxstroke();
	了解判断点是否在路径中（知道有）
	contextisPointInPath(x,y);
    //isPointInPath() 方法返回 true，如果指定的点位于当前路径中；否则返回 false。
    //判断x,y坐标的点是否在当前的路径中。
	了解文本宽度计算（知道有）
	contextmeasureText(text)width;
   如果以后做canvas游戏方向开发深入学习可以扩展内以下容：
	setTransform()  将当前转换重置为单位矩阵。然后运行 transform()
	transform() 替换绘图的当前转换矩阵
	globalCompositeOperation   设置或返回新图像如何绘制到已有的图像上
	像素操作

六、 konva库的学习：
在开发过程中，为了提高开发效率。简化开发过程，通常会用一些别人封装好的一些库来编写代码。konva就是其中一个。
   Konva的整体理念
	舞台的概念的引入。整个视图看做是一个舞台 stage
	舞台中可以绘制很多个层 layer
	layer下面可以有很多的group
	group下面可以有 矩形、图片、其他形状等
	参看：快速上手文档---查看翻译文档
                  Stage
                    |
             +------+------+
             |             |
           Layer         Layer
             |             |
       +-----+-----+     Shape
       |           |
     Group       Group
       |           |
       +       +---+---+
       |       |       |
    Shape   Group    Shape
               |
               +
               |
             Shape
