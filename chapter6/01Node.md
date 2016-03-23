# NodeJS第一天

## Node.js介绍

> Node.js is a JavaScript runtime built on **Chrome's V8 JavaScript engine**. Node.js uses an **event-driven**, **non-blocking I/O model** that makes it **lightweight and efficient**. Node.js' package ecosystem, npm, is the largest ecosystem of open source libraries in the world.

NodeJS 不是JavaScript,是一个可以解析和执行javascript的容器(平台).

## 安装与配置Node.js开发环境

#### 普通方式安装

访问官方网站[nodejs.org](http://nodejs.org)或者[github.com/nodesource/distributions](https://github.com/nodesource/distributions)，查看Node的最新版本和安装方法。

#### 使用nvm版本管理工具
如果想在同一台机器，同时安装多个版本的node.js，就需要用到版本管理工具nvm。

`cmd`下打开系统属性输入`sysdm.cpl`

#### NVM 的使用

| 终端下命令     | 代表意义    |
| :------------- | :------------- |
| `nvm list`       | 查看 nvm 中已安装的 Node.js 版本       |
| `nvm use 版本号`       | 使用指定版本号的 Node.js      |
| `nvm install 版本号`       | 安装指定版本号的 Node.js       |
| `nvm uninstall <version>`       | 删除指定版本号的 Node.js       |

**常用CMD命令**

| 终端下命令     | 代表意义    |
| :------------- | :------------- |
| `cd（change directory）`       | 切换目录       |
| `md（make directory）`       | 新建目录      |
| `rd（remove directory）`       | 删除非空目录    |
| `dir（directory）`       | 查看目录中的条目       |
| `ren（rename）`       | 重命名文件      |
| `del（delete）`       | 删除文件    |
| `cls（clear screen）`       | 清屏       |
## Node.js初体验

#### 基于命令台的hello world

在终端下输入`node`进入REPL(READ-EVAL-PRINT-LOOP),方便测试JavaScript代码的运行环境
在window下按两次<kbd>ctrl</kbd>+<kbd>c</kbd>或者`.exit`退出

- 和浏览器`console`控制台基本一样
- 直接运行函数
- 使用`_`下划线字符使用,表示上一个命令的返回结果

#### 运行一个脚本文件

`node`+`文件名` 命令
可以执行当前路径中的JS文件,也只可以传入一个路径
#### 快速写出一个服务器程序
#### 全局对象

NODE`REPL`下的全局对象有
- `global`类似于浏览器下的全局对象`window`
- `process`该对象表示Node所处的当前进程，允许开发者与该进程互动。
- `__dirname`指向当前运行的脚本所在的目录。和`__filename`指向当前运行的脚本文件名。
- `setInteval`和`setTimeout`
- `clearInteval`和`clearTimeout`
- `console`
- `require()`：用于加载模块。
- `Buffer()`：用于操作二进制数据。

```javascript
/**
 * 统计代码执行时间,
 * @method time
 * @param  {[type]} 'timer' [description]
 * @return {[type]}         [description]
 */
console.time('timer');

//javascript代码

console.timeEnd('timer');

```

## 模块化开发

**什么是模块**

在CommonJS规范中,一个文件就是一个模块

### 模块化方式演变计算器
#### 全局函数直接写到html文件中
#### 将js代码提取出来放到单独的js文件中
#### 封装对象方式解决全局函数面临的''问题
#### 给对象加入独立的作用空间

### CommonJS
#### 模块引用
#### 模块定义
#### 模块标识
## Node.js中的模块实现

#### 核心模块
#### 文件模块
#### 路径分析
#### 文件定位
#### 编译执行
## npm模块管理工具

## Node.js的运行机制

#### Node.js旨在解决的问题
#### 进程和线程
#### JavaScript是单线程的
#### Node.js的事件驱动与异步IO
## Node.js原理解析

#### 进程和线程
#### 事件驱动
#### 无阻塞I/O模型
