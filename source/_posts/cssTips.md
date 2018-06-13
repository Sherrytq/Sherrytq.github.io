---
title: CssTips
category: front-end
tag: css
archive: frontEnd
---
### 1. 三角形实现
```
<div class="test"></div> 
.test{
  border:1px solid #000;
  width: 200px;
  height:400px;
  position: absolute;
  left: 0;
  z-index: 10;
  box-sizing: border-box;
  list-style: none;
  padding: 0.5rem 0;
  margin: 0;
  background: #fff;
}
.test:before {
  content: "";
  position: absolute;
  top: -.43em;
  left: 1em;
  width: 0;
  height: 0;
  padding: .4em;
  background: white;
  border: inherit;
  border-right: 0;
  border-bottom: 0;
  -webkit-transform: rotate(45deg);
  transform: rotate(45deg);
}
```
参考链接：   
[使用CSS绘制箭头](http://simaq.github.io/css/2014/03/30/implementation-of-arrows-with-css/)  
[div+css实现带三角箭头提示框](http://www.cnblogs.com/undefined000/archive/2012/09/24/2700426.html)
### 2.  图片裁剪：  `` clip: rect(0, 0, 0, 0);``
### 3. [CSS @supports](http://www.webhek.com/post/css-supports.html)  
    火狐浏览器 谷歌浏览器 Opera浏览器
    最近刚刚添加了一项新的功能——在CSS里支持`@supports`标记、在JavaScript里支持`CSS.supports`函数，用来检测浏览器是否支持某个期望的样式功能。
### 4. em px  => 1em = 16px 
### 5. `mark` 标签 突出显示某个部分
### 6. `display` 属性
![image.png](http://upload-images.jianshu.io/upload_images/8952934-2c69e5fe0b3f42a1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
### 7. oo css的作用和注意事项
![](https://i.imgur.com/GkpMsHp.png)

8. 文字过多，显示`...`的效果
```css
.title{
text-overflow: ellipsis;
overflow: hidden;
white-space: nowrap;
max-width:70%; //可省或者固定宽度 width: 60px;
display: inline-block;
}
```

### 其中textarea元素的高度为80px，而它的父元素div高度为84px，为什么会多出4px呢？

设textarea为 display: block;

### loading 动画效果
```
	<div class="loading ball-pulse">
		<div></div> 
		<div></div> 
		<div></div> 
		<span>加载中...</span>
	</div>
```

```
.loading.ball-pulse>div {
    background-color: #999;
    width: 8px;
    height: 8px;
    border-radius: 100%;
    margin: 1px;
    animation-fill-mode: both;
    display: inline-block;
}

.loading.ball-pulse>div:first-child {
    animation: scale .75s -.24s infinite cubic-bezier(.2,.68,.18,1.08);
}

.loading.ball-pulse>div:nth-child(2) {
    animation: scale .75s -.12s infinite cubic-bezier(.2,.68,.18,1.08);
}

.loading.ball-pulse>div:nth-child(3) {
    animation: scale .75s 0s infinite cubic-bezier(.2,.68,.18,1.08);
}

@keyframes scale{
	0%{
		transform:scale(1);
		opacity:1
	}
	45%{
		transform:scale(.1);
		opacity:.7
	}
	80%{
		transform:scale(1);
		opacity:1
	}
}
```

### 圆环旋转
```
.animateCircle {
	-webkit-animation:circle 1s infinite linear;/*匀速 循环*/
}

@-webkit-keyframes circle{
0%{ transform:rotate(0deg); }
100%{ transform:rotate(-360deg); }
}
```

### 文本只有两行
[https://segmentfault.com/q/1010000005614773](https://segmentfault.com/q/1010000005614773 "https://segmentfault.com/q/1010000005614773")

### 强制换行
[http://www.iwms.net/n1919c40.aspx](http://www.iwms.net/n1919c40.aspx "http://www.iwms.net/n1919c40.aspx")



