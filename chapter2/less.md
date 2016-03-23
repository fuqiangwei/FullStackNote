---
Author: fuqiangwei
Date:   2016-01-17 18:17:39
Last Modified by:   fuqiangwei
Last Modified time: 2016-01-18 16:35:06
---

# Bootstrap定制

## LESS概述

### 什么是LESS

+ 动态样式语言
+ LESS将CSS赋予了动态语言的特性(变量,继承,运算,函数),让样式文件(CSS)更加容易编写和维护。
+ LESS需要编译后才能在客户端(浏览器)上运行,也可以Node.js或者Rhino在服务端运行.

### 使用LESS

1. 在客户端使用Less

在HTML页面中引入`*.less`文件，同时引入一个LESS转换程序`less.js`，让客户端同时下载`.html/*.less/less.js`转换器，在客户端浏览器中运行`less.js`把*.less转换为CSS样式

2. 在服务器端使用Less

使用命令行工具(less编译器)，把`*.less`编译为`*.css`，在HTML页面中，直接引入编译好的.css文件即可.

  使用步骤
  1. 在服务器端安装服务器端的JS解释器`Node.JS`
  2. 服务器端安装Less编译器程序 `lessc`
  3. 运行Node，执行lessc转换程序，把一个`*.less`文件编译为一个相应的css文件

      1. 直接在命令行中执行 `node lessc *.less > *.css`

      2. 把lessc编译器配置为WebStorm中的FileWatcher，只要用户在WS中创建并保存了一个.less文件，修改任意的less文件并保存，即会自动编译出对应的.css文件.
      3. Less FileWatcher只对当前项目有效；如果创建了新项目，必须重新配置一遍FileWatcher

## LESS语法

#### 语法

+ less完整的支持CSS所有的语法,在less文件中可以编写任意合法的css代码
+ less支持单行/多行注释，但只有多行注释会被编译到.css文件中去


#### 变量

#### 带参混合

#### 嵌套规则

#### 运算

#### 内置函数

Less 内置了多种函数用于转换颜色、处理字符串、算术运算等.
ceil( 参数 )
floor( 参数 )
hsl(色相,  饱和度,  明度)   把一个HSL颜色转换为RGB颜色
lighten(颜色, 明度)  把指定的颜色变亮指定的百分比
darken(颜色, 明度)   把指定的颜色变暗指定的百分比


#### 命名空间

#### 作用域

#### 注释

#### 文件导入

在传统CSS文件中，也可以实现文件的导入.`@import '*.css'`

> CSS文件中声明@import会导致浏览器在加载完当前css之后再次发起请求，获取服务器端另一个css文件，增加请求次数，且减慢页面渲染效率，故不推荐使用。

在Less文件中 @import "xx.less" 可以实现在服务器端就把被引入的文件内容拼合在当前生成的.css中，多个这样的@import最终可以生成一个大的完整的css文件，供客户端一次性的全部下载，不存在性能问题

### 定制Bootstrap

1. 删除不需要的组件和插件.在bootstrap.less文件中，把不必要的@import注释掉即可。
2. 修改需要的组件默认的样式.在variables.less文件中，修改特定的Less变量值.
3. 深度定制某个组件的实现细节.修改需要的组件相对应的.less文件,比如dropdown.less、modal.less.
