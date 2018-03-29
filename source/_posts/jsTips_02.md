---
title: JSTIPS_02
category: front-end
tag: js
archive: frontEnd
---
### 1. 状态码
500 Internet server Error 网络服务器出错 服务器挂了
502 Bad gateway 防火墙问题
400(错误请求)服务器不理解请求的语法。
403 Forbidden 传入的参数有误
404 Not Found 
301(永久移动)请求的网页已永久移动到新位置。服务器返回此响应(对 GET 或 HEAD 请求的响应)时，会自动将请求者转到新位置。您应使用此代码告诉 Googlebot 某个网页或网站已永久移动到新位置。
302(临时移动)服务器目前从不同位置的网页响应请求，但请求者应继续使用原有位置来响应以后的请求。此代码与响应 GET 和 HEAD 请求的 301 代码类似，会自动将请求者转到不同的位置，但您不应使用此代码来告诉 Googlebot 某个网页或网站已经移动，因为 Googlebot 会继续抓取原有位置并编制索引。
303(查看其他位置)请求者应当对不同的位置使用单独的 GET 请求来检索响应时，服务器返回此代码。对于除 HEAD 之外的所有请求，服务器会自动转到其他位置
304(未修改)自从上次请求后，请求的网页未修改过。服务器返回此响应时，不会返回网页内容。
200 OK 
### 2. 3次握手协议
连接要3次 断开要4次  SYN 同步 ACK 确认
![image.png](http://upload-images.jianshu.io/upload_images/8952934-e02349426b310b96.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
### 3. [js 的面向对象](https://www.cnblogs.com/Leo_wl/p/5734794.html) 
http://blog.csdn.net/jcx5083761/article/details/8606576
封装 继承 多态（同一个动作的不同相应）
>ps: 可以把那些不变的属性和方法，直接定义在prototype对象上。
### 4. json 对象和json 之间的转换
>json(javascript object notation) 是一种轻量级的数据交换格式。它是基于js 的一个子集。数据格式简单，易于读写，占用带宽小，如：{"age":"12","name":"back"}

>json 字符串转为json对象：
var obj = eval('('+ str +')');
var obj = str.parseJSON();
var obj = JSON.parse(str);

>JSON对象转换为JSON字符串
var last = obj.toJSONString();
var last = JSON.stringify(obj);
### 5. [清除浮动](http://lightcss.com/all-about-clear-float/)
-**在末尾增加一个<div style="clear:both"></div>**
-**使用：after 伪类**
```
.clearfix:after{content:".";display:block;height:0;clear:both;visibility:hidden}
.clearfix{zoom:1;}
.clearfix{*display:inline-block}
.clear,.cls{clear:both}
```
### 6. [call apply 和bind 的区别](http://www.cnblogs.com/coco1s/p/4833199.html)
相同点： 都可以改变this的指向
不同点：fn.apply(obj,[100,10])
              fn.call(obj,100,10)
### 7. [一次完整http 事务的过程](https://www.linux178.com/web/httprequest.html)
>域名解析 --> 发起TCP的3次握手 --> 建立TCP连接后发起http请求 --> 服务器响应http请求，浏览器得到html代码 --> 浏览器解析html代码，并请求html代码中的资源（如js、css、图片等） --> 浏览器对页面进行渲染呈现给用户
### 8. [正则表达式](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Guide/Regular_Expressions#note)

### 9. [事件冒泡](http://caibaojian.com/javascript-stoppropagation-preventdefault.html)
![image.png](http://upload-images.jianshu.io/upload_images/8952934-7465e97753a5c69a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 10. [ul 中要对每个li 进行处理](http://m.jb51.net/article/85734.htm)
jq 中要应用到 each 对每个进行处理
纯js中需要用到for循环
另外点击事件是可能造成事件冒泡的，在下一次的点击事件中，点击目标会成为全局



 




