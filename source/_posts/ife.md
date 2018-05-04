---
title: 百度前端学院2016练习
category: front-end
tag: [css,js]
archive: front-end
---

## 练习链接
[ http://ife.baidu.com/2016/task/all?qq-pf-to=pcqq.group]( http://ife.baidu.com/2016/task/all?qq-pf-to=pcqq.group " http://ife.baidu.com/2016/task/all?qq-pf-to=pcqq.group")

### Box-shadow
>box-shadow: h-shadow v-shadow blur spread color inset;
### 空格 `&nbsp;`
### 通用样式 `normalize.css` 
* link： https://necolas.github.io/normalize.css/8.0.0/normalize.css	
* `cnpm install normalize.css`

### Table 边框 
`border-collapse` 属性设置是否将表格边框折叠为单一边框：
```html
table
{
 border-collapse:collapse;
 }
table,th, td
{
 border: 1px solid black;
}
<table border="1">
  <thead>
    <tr>
      <th>Month</th>
      <th>Savings</th>
    </tr>
  </thead>

  <tfoot>
    <tr>
      <td>Sum</td>
      <td>$180</td>
    </tr>
  </tfoot>

  <tbody>
    <tr>
      <td>January</td>
      <td>$100</td>
    </tr>
    <tr>
      <td>February</td>
      <td>$80</td>
    </tr>
  </tbody>
</table>
```
### css 选择器 `first-child`

### Input radio 样式设置
* 用图片样式进行覆盖 可以设置透明度  
* css设置样式
> 参考连接   
[https://www.cnblogs.com/sakura-panda/p/7065449.html](https://www.cnblogs.com/sakura-panda/p/7065449.html "https://www.cnblogs.com/sakura-panda/p/7065449.html")
[https://codepen.io/AngelaVelasquez/pen/Eypnq](>https://codepen.io/AngelaVelasquez/pen/Eypnq "https://codepen.io/AngelaVelasquez/pen/Eypnq")

 
```html:
<div for="male" class="radioBtn">
    <input type="radio" id="f-option" name="male">
    <label for="f-option">男</label>
    <div class="check"></div>
</div>

<div for="female" class="radioBtn">
    <input type="radio" id="f-option" name="female">
    <label for="f-option">女</label>
    <div class="check"></div>
</div>
```
```css: 
.radioBtn{
  color: #AAAAAA;
  display: inline-block;
  position: relative;
  float: left;
  height: 100px;
}

.radioBtn input[type=radio]{
  position: absolute;
  visibility: hidden;
}

.radioBtn label{
  display: inline-block;
  position: relative;
  font-weight: 300;
  font-size: 1.35em;
  padding: 25px 25px 25px 80px;
  margin: 10px auto;
  height: 30px;
  z-index: 9;
  cursor: pointer;
  -webkit-transition: all 0.25s linear;
}

.radioBtn :hover label{
	color: #FFFFFF;
}

.radioBtn .check{
  display: block;
  position: absolute;
  border: 5px solid #AAAAAA;
  border-radius: 100%;
  height: 25px;
  width: 25px;
  top: 30px;
  left: 20px;
	z-index: 5;
	transition: border .25s linear;
	-webkit-transition: border .25s linear;
}

.radioBtn :hover .check {
  border: 5px solid #FFFFFF;
}

.radioBtn .check::before {
  display: block;
  position: absolute;
	content: '';
  border-radius: 100%;
  height: 15px;
  width: 15px;
  top: 5px;
	left: 5px;
  margin: auto;
	transition: background 0.25s linear;
	-webkit-transition: background 0.25s linear;
}

input[type=radio]:checked ~ .check {
  border: 5px solid #0DFF92;
}

input[type=radio]:checked ~ .check::before{
  background: #0DFF92;
}

input[type=radio]:checked ~ label{
  color: #0DFF92;
}
```

###  三栏式布局 
左边：float:left;  
右边：float:right;  
中间：用margin 控制距离；  
父选择器：清除浮动

### 清除浮动
```
.clearfix:after {
  content: ".";
  display: block;
  height: 0;
  clear: both;
  visibility: hidden;
}
.clearfix{zoom:1;}
.clearfix {
  *display: inline-block;
}
.clear,.cls {
  clear: both;
}
```

### 页面水平 垂直 居中
```
/*方法一：知道高度和宽度*/
.sub {
    width: 400px;
    height: 200px;
    background: #ccc;
    position: absolute;
    left: 50%;
    top: 50%;
    margin-left: -200px;
    margin-top: -100px;
}
/*方法二： 不知道高度和宽度*/
.container {
    width: 400px;
    height: 200px;
    background-color: #ccc;
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%,-50%);
}
```
## 参考链接
[http://https://css-tricks.com/centering-css-complete-guide/(非常详细！)](http://https://css-tricks.com/centering-css-complete-guide/)




