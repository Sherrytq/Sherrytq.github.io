---
title: CSS居中
category: front-end
tag: css
archive: frontEnd
---

### 1. 大包小 只是水平居中 margin:auto dispaly:table
```
<style>
  #ex2_container { width:200px; height：300px; background-color:yellow; }
  #ex2_content {  height:100px; width:100px; margin:0px auto; background-color:gray; color:white; display:table; }
</style>
<div id="ex2_container"><div id="ex2_content">Hello World</div></div>
```
![image.png](http://upload-images.jianshu.io/upload_images/8952934-e2fd3222e3aa3a7d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 2 translate(-50%,-50%) 
```
<style>
  #ex3_container { width:200px; height:200px; background-color:yellow; position:relative; }
  #ex3_content {height:100px; width:120px; left:50%; top:50%; transform:translate(-50%,-50%); -webkit-transform:translate(-50%,-50%); background-color:gray; color:white; position:absolute; }
</style>
<div id="ex3_container"><div id="ex3_content">Hello World</div></div>
```
![image.png](http://upload-images.jianshu.io/upload_images/8952934-89499a3986ef1998.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 3. 绝对定位居中
```
<style>
#ex2_container {
  width: 300px;
  height:200px;
  background-color:yellow;
  position: relative;
/*   text-align:center; */
}
#ex2_content {
  width:100px;
  height:100px;
  background-color:grey;
/* width: 50%;
  height: 50%; */
  overflow: auto;
  margin: auto;
  position: absolute;
  top: 0; left: 0; bottom: 0;   right: 0;
}
</style>
<div id="ex2_container">
  <div id="ex2_content">Hello World</div>
</div>
```
![image.png](http://upload-images.jianshu.io/upload_images/8952934-c3b998eede508e2e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
### 4. 用于mask 布局
```
<style>
#ex2_container,#is-Fixed {
  position:fixed;
  background-color:yellow;
  top:0;
  right:0;
  left:0;
  bottom:0;
}
#ex2_container #is-Fixed {
  width: 100px;
  height: 100px;
 */ width: 60%; 
  height: 60%;
  min-width: 400px;
  max-width: 500px;*/
  overflow: auto;
  margin: auto;
  z-index: 999;
  background-color:grey;
}
</style>
<div id="ex2_container">
  <div id="is-Fixed">Hello World</div>
</div>
```
![image.png](http://upload-images.jianshu.io/upload_images/8952934-de8a7a5d8fbb5b43.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

## 参考文献:   
[CSS 居中大全](https://jinlong.github.io/2013/08/13/centering-all-the-directions/)  
[CSS制作水平垂直居中对齐](https://www.w3cplus.com/css/vertically-center-content-with-css)






