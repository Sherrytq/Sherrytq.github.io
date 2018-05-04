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


