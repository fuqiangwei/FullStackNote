-  模板引擎
    - 原理剖析
    - 流行模板引擎
    - artTemplate
-  同源&跨域
    - 同源
    - 跨域
    - 跨域方案
    - JSONP
    - jQuery中的JSONP
    - JSONP
-  综合练习  

第9章模板引擎
9.1	原理剖析
9.2	流行模板引擎
9.3	artTemplate

第10章同源&跨域
10.1	同源
同源策略是浏览器的一种安全策略，所谓同源是指，域名，协议，端口完全相同。
10.2	跨域
不同源则跨域
例如http://www.example.com/
http://api.example.com/detail.html	不同源	域名不同
https//www.example.com/detail.html	不同源	协议不同
http://www.example.com:8080/detail.html	不同源	端口不同
http://api.example.com:8080/detail.html	不同源	域名、端口不同
https://api.example.com/detail.html	不同源	协议、域名不同
https://www.example.com:8080/detail.html	不同源	端口、协议不同
http://www.example.com/detail/index.html	同源	只是目录不同
10.3	跨域方案
1、顶级域名相同的可以通过domain.name来解决，即同时设置 domain.name = 顶级域名（如example.com）
2、document.domain + iframe
3、window.name + iframe
4、location.hash + iframe
5、window.postMessage()
10.4	JSONP
10.5	jQuery中的JSONP
第11章综合练习
