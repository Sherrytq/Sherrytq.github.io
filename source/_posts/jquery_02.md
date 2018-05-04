---
title: JS 和 Jquery 中的高和宽
category: front-end
tag: [js, jquery]
archive: front-end
---

### window 和 document 的区别
* window 对象表示浏览器打开的窗口
* window 对象可以省略

* document 对象是 window 对象的一部分
* 浏览器的HTML 文档成为 document 对象

### window.location 和 document.loaction 的区别
* 都是引用的Location 对象 表示该窗口中当前显示文档的URL
* window.location === document.location

### window.innerHeight 与 window。outerHeight
 
![](https://i.imgur.com/rQ7oFRy.png)

### window.screen 包含有关用户屏幕的信息

screen.height 和 screen.availHeight 
screenTop screenLeft screen.width screen.availWidth 

![](https://i.imgur.com/1vBvhjy.png)
![](https://i.imgur.com/DesM5SG.png)

### 兼容性问题
* window 
innerHeight IE9 以上
![](https://i.imgur.com/xwQea1b.png)
针对不同浏览器可视区域的宽高
```
var w= docuemnt.documentElement.clientWidth || document.body.clientWidth;
var h= docuemnt.documentElement.clientHeight || document.body.clientHeight;
```
### document 
* 与client 相关的宽高
 clientWidth 和 clientHeight  
 * 可视部分的宽高！
 * padding+ content
![](https://i.imgur.com/qhnrbXr.png)
![](https://i.imgur.com/xP7C9eo.png)
![](https://i.imgur.com/azyhzpl.png)

clientLeft 和 clientTop
* 返回元素周围边框的厚度， 如果不指定一个边框或者不定位该元素，则值为0 
* 读取元素的border的宽度和高度
clienTop = border-top 的border-width
clienLeft = border-left 的border-width

* 与offset 相关的宽高
offsetWidth 与 offsetHeight
* 指元素的border + padding + content 的宽度和高度
* 该属性和期内部的内容是否超出元素大小无关，只与本来设定的border 以及width和height有关
![](https://i.imgur.com/5RAaYXc.png)

offsetLeft 和 offsetTop
![](https://i.imgur.com/2YzpoRD.png)
![](https://i.imgur.com/PewEehF.png)
![](https://i.imgur.com/2inBGun.png)

* 与scroll 先关
![](https://i.imgur.com/OME9t93.png) 
![](https://i.imgur.com/wWLBCP7.png)
![](https://i.imgur.com/tkEym5b.png)

### documentElement 和 body 的关系

![](https://i.imgur.com/4ILLeKO.png)

### `event` 的五个坐标

 ![](https://i.imgur.com/dnT8f2P.png)

### `getBoundingClientRect()`

![](https://i.imgur.com/Z6cW3ae.png)

###  滚动到底部和顶部

```
 <script type="text/javascript">
   function scrollBottomOrTop(){
    var clients = window.innerHeight || document.documentElement.clientHeiht || document.body.clientWidth;
    var scrollTop = document.body.scrollTop;
    var wholeHeight = document.body.scrollHeight;
    if(clients + scrollTop >= wholeHeight){
        alert('我已经滚动到底部了')
    }else if(scrollTop == 0 ){
        alert("我已经滚动到顶部了")
    }
  }

  window.onscroll = scrollBottomOrTop;
 </script>

```

```
<script type="text/javascript">
  var divscroll = document.getElementById('testDiv');
  function scrollBottomOrTop(){
    var scrollTop = divscroll.scrollTop;
    var wholeHeight = divscroll.scrollHeight;
    var divHeight = divscroll.clientHeight;
    if(divHeight + scrollTop >= wholeHeight){
        alert('我已经滚动到底部了')
    }else if(scrollTop == 0 ){
        alert("我已经滚动到顶部了")
    }
  }

  divscroll.onscoll = scrollBottomOrTop
</script>
```
### 计算滚动轴的宽度
document.offsetWidth - document.clientWidth

###  jq部分的宽高
![](https://i.imgur.com/K4uPDOD.png)
![](https://i.imgur.com/gLhvcJk.png)
![](https://i.imgur.com/9X9kLoa.png)
![](https://i.imgur.com/YeVTa3S.png)
![](https://i.imgur.com/6nqYQwB.png)
![](https://i.imgur.com/7kiJsc5.png)
![](https://i.imgur.com/87GZ2qN.png)
![](https://i.imgur.com/hC9aUYs.png)

```
  $(windwo).scroll(function(){
    var scrollTop = $(window).scrollTop();
    var ks_arae = $(window).height();
    var wholeHeight = $(document).height();
    if(ks_arae + scrollTop >= wholeHeight){
      alert('滚动到底部啦')
    }else if(scrollTop == 0){
      alert("滚动到顶部啦")
    }
  })
```


  



