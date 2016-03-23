-  AJAX编程
    - 异步
    - XMLHttpRequest
        - 请求
        - 响应
        - API详解
    - XML
        - 语法规则
        - XML示例
    - JSON
        - 语法规则
        - JSON解析
    - 兼容性
    - 封装AJAX工具函数
    - jQuery中的Ajax
    - 文件引入
    - 超全局变量
    - 表单处理
    - 常用PHP函数
    - 函数

## AJAX编程

#### 什么是Ajax
AJAX即Asynchronous Javascript And XML（异步`JavaScript`和`XML`) ，AJAX 不是一门的新的语言，而是对现有技术的综合利用。
- 本质是在HTTP协议的基础上以异步的方式与服务器进行通信。
    - 节省用户操作时间，提高用户体验，减少数据请求
    - 获取数据，进行数据交互

#### 异步
>指某段程序执行时不会阻塞其它程序执行，其表现形式为程序的执行顺序不依赖程序本身的书写顺序，相反则为同步。

其优势在于不阻塞程序的执行，从而提升整体执行效率。

####	XMLHttpRequest对象

```Javascript

var xhr = null;
try {
  xhr = new XMLHttpRequest();
} catch (e) {
  xhr = new ActiveXObject('Microsoft.XMLHTTP');//兼容IE6
}

```
XMLHttpRequest可以以异步方式的处理程序。
浏览器内建对象，用于在后台与服务器通信(交换数据) ，由此我们便可实现**对网页的部分更新**，而不是刷新整个页面。
下面是一个简单的例子

由于XMLHttpRequest本质基于HTTP协议实现通信，所以结合HTTP协议和上面的例子我们分析得出如下结果：
8.2.1	请求
HTTP请求3个组成部分与XMLHttpRequest方法的对应关系
1、请求行

2、请求头

get请求可以不设置
3、请求主体

注意书写顺序
8.2.2	响应
HTTP响应是由服务端发出的，作为客户端更应关心的是响应的结果。
HTTP响应3个组成部分与XMLHttpRequest方法或属性的对应关系。
由于服务器做出响应需要时间（比如网速慢等原因），所以我们需要监听服务器响应的状态，然后才能进行处理。

1、获取状态行（包括状态码&状态信息）


2、获取响应头

3、响应主体

我们需要检测并判断响应头的MIME类型后确定使用request.responseText或者request.responseXML
8.2.3	API详解
xhr.open() 发起请求，可以是get、post方式
xhr.setRequestHeader() 设置请求头
xhr.send() 发送请求主体get方式使用xhr.send(null)
xhr.onreadystatechange = function () {} 监听响应状态
xhr.readyState = 1时，
xhr.readyState = 2时，
xhr.readyState = 3时，
xhr.readyState = 4时，
xhr.status表示响应码，如200
xhr.statusText表示响应信息，如OK
xhr.getAllResponseHeaders() 获取全部响应头信息
xhr.getResponseHeader('key') 获取指定头信息
xhr.responseText、xhr.responseXML都表示响应主体
注：GET和POST请求方式的差异
1、GET没有请求主体，使用xhr.send(null)
2、GET可以通过在请求URL上添加请求参数
3、POST可以通过xhr.send('name=itcast&age=10')
4、POST需要设置

问题？如何获取复杂数据呢？
8.3	XML
XML是一种标记语言，很类似HTML，其宗旨是用来传输数据，具有自我描述性（固定的格式的数据）。

8.3.1	语法规则
1、必须有一个根元素
2、不可有空格、不可以数字或.开头、大小写敏感
3、不可交叉嵌套
4、属性双引号（浏览器自动修正成双引号了）
5、特殊符号要使用实体
6、注释和HTML一样
虽然可以描述和传输复杂数据，但是其解析过于复杂，所以实现开发已经很少使用了。
8.3.2	XML示例
详见代码
8.4	JSON
即 JavaScript Object Notation，另一种轻量级的文本数据交换格式，独立于语言。
8.4.1	语法规则
1、数据在名称/值对中
2、数据由逗号分隔(最后一个健/值对不能带逗号)
3、花括号保存对象方括号保存数组
4、使用双引号
8.4.2	JSON解析
JSON数据在不同语言进行传输时，类型为字符串，不同的语言各自也都对应有解析方法，需要解析完成后才能读取
1、Javascript 解析方法
eavl()、JSON对象  JSON.parse()、JSON.stringify()；
JSON兼容处理json2.js
2、PHP解析方法
json_encode()、json_decode()
总结：JSON体积小、解析方便且高效，在实际开发成为首选。
8.5	兼容性
IE5、IE6中使用 ActiveObject("Microsoft.XMLHTTP")
如下图

关于IE的兼容方面，了解即可。
8.6	封装AJAX工具函数
为了提升我们的开发效率，我们自已将XMLHttpRequest封装成一个函数。
8.7	jQuery中的Ajax
