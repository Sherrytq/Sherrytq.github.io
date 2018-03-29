---
title: JSTIPS_03
category: front-end
tag: js
archive: frontEnd
---

### 1.[js jq 中获得data*属性](https://segmentfault.com/a/1190000005770912)

### 2.显示keyCode

![image.png](http://upload-images.jianshu.io/upload_images/8952934-345b06bd113dd2d8.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 3.阻止右键
```
document.oncontextmenu  = function(){
    return false;
}
```
### 4.[获取目标的当位置](http://shanmao.me/web/js/pagex-clientx-offsetx-layerx-de-qu-bie)
x:设置或者是得到鼠标相对于目标事件的父元素的外边界在x坐标上的位置。 
clientX:相对于客户区域的x坐标位置，不包括滚动条，就是正文区域。 
offsetx：设置或者是得到鼠标相对于目标事件的父元素的内边界在x坐标上的位置。 
screenX:相对于用户屏幕  
PageY=clientY+scrollTop-clientTop;(只讨论Y轴,X轴同理,下同)
页面上的位置=可视区域位置+页面滚动条切去高度-自身border高度,还是直接上图比较清楚
(http://blog.csdn.net/xuantian868/article/details/3116442)
### 5.[水平垂直居中](https://www.w3cplus.com/css/vertically-center-content-with-css)
### 6.[jQuery中position()与offset()区别](http://www.cnblogs.com/tianguook/p/4079542.html)
position()获取相对于它最近的具有相对位置(position:relative或position:absolute)的父级元素的距离，如果找不到这样的元素，则返回相对于浏览器的距离。
offset()始终返回相对于浏览器文档的距离，它会忽略外层元素。
下边看个简单的例子，这里外层的div元素(position:relative)仅一个：
```
<div id = "outer" style="width:200px;position:relative;left:100px;">
  <div id="inner" style="position:absolute;left:50px;top:60px;"></div>
</div>
//获取相对于最近的父级(position:relative或position:absolute)的位置
var vposition = $("#inner").position();
alert(vposition.left);//输出：50
alert(vposition.top);//输出：60
var voffset = $("#inner").offset();
alert(voffset.left);//输出：$("#outer").offset().left+50
alert(voffset.top);//输出：$("#outer").offset().top+60
```
在不同浏览器中,offset()得到的相对于浏览器的位置不同，相信你看了上边相应的注释，已经掌握了position()同offset()方法的区别。
### 7. Li 滚动
```
//html
<ul id="dpdataul">
        <li>hhhaha1</li>
        <li>hhhah2a2</li>
        <li>hhhaha3</li>
        <li>hhhaha4</li>
        <li>hhhaha5</li>
        <li>hhhaha6</li>
        <li>hhhaha7</li>
        <li>hhhaha8</li>
        <li>hhhaha9</li>
        <li>hhhaha10</li>
</ul>
<span id='up'>up</span>
 <span id='down'>down</span>
```
```
//css
ul{
  height: 30px;
  width: 300px;
  overflow: hidden;
}
ul li{
  height: 30px;
  line-height: 30px;
}
```
```
//js
$("#dpdataul").scrollTop(150);
$("#up").click(function(){
      var _this = this;
    $("#up").click(function(){
      binddpdatascroll(30);
      return false;
    });
    $("#down").click(function(){
      binddpdatascroll(-30);
      return false;
    });
})
function binddpdatascroll(n){ //大盘滚动
    var dpdataul = $("#dpdataul");
    var nowstop = dpdataul.scrollTop();
    dpdataul.animate({
      scrollTop:nowstop + n
    }, 200, function (){
      nowstop2 = dpdataul.scrollTop();
      if( nowstop2 <= 0 ){
        dpdataul.scrollTop(150);
        nowstop = 150;
      }
      if( nowstop2 > 240 ){
        dpdataul.scrollTop(120);
        nowstop = 120;
      }
    } );
    return false;
  }
```
### 8. 同源策略 jsonp ajax
由于同源策略的限制，XmlHttpRequest只允许请求当前源（域名、协议、端口）的资源，为了实现跨域请求，可以通过script标签实现跨域请求，然后在服务端输出JSON数据并执行回调函数，从而解决了跨域的数据请求，这就是jsonp的核心。
jsonp原理：
- 首先在客户端注册一个callback, 然后把callback的名字传给服务器。
- 服务器先生成 json 数据。 然后以 javascript 语法的方式，生成一个function , function 名字就是传递上来的参数 jsonp. 最后将 json 数据直接以入参的方式，放置到 function 中，这样就生成了一段 js 语法的文档，返回给客户端。
- 客户端浏览器，解析script标签，并执行返回的 javascript 文档，此时数据作为参数，传入到了客户端预先定义好的 callback 函数里.（动态执行回调函数）
![image.png](http://upload-images.jianshu.io/upload_images/8952934-134c9f19bb0eac54.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 9.[倒计时](https://segmentfault.com/q/1010000000435922)

### 10.[js中设置元素class的三种方法小结](http://www.jb51.net/article/28118.htm)




