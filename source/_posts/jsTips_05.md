---
title: JsTips
category: front-end
tag: js
archive: front-end
---

### js  委托 delegate
### jq ajax 请求
   $.getJSON()
### 当两个数据都返回再回调
    `$.when`
    `.done`
### 跨域问题  
   参考链接： [ajax跨域，这应该是最全的解决方案了](ajax跨域，这应该是最全的解决方案了 "https://segmentfault.com/a/1190000012469713") 
### JavaScript 运行机制详解：再谈Event Loop
[http://www.ruanyifeng.com/blog/2014/10/event-loop.html](http://www.ruanyifeng.com/blog/2014/10/event-loop.html "http://www.ruanyifeng.com/blog/2014/10/event-loop.html")
### 原型和原型链
```
function foo(){
	var x = 10; 
	return function bar(){
		console.log(x)
	};
}

var returnedFunction = foo();
var x = 20;

returnedFunction();  //10
```
```
var x = 10; 
function foo(){
	console.log(x)
}

var b = function(funArg) {
	var x = 20;
	funArg();
}
 
b(foo);  //10
```
```
for(var i = 0; i< 5; i++){
	setTimeout(function(){
           console.log(i)
	},i*1000)
}  // 55555
```
```
for(var i = 0; i< 5; i++){
	(function(i){
		setTimeout(function(){
           console.log(i)
		},i*1000)
	})(i)
}  // 每一秒 0 , 1, 2, 3, 4
```
```
for(var i = 0; i< 5; i++){
	(function(){
		setTimeout(function(){
           console.log(i)
		},i*1000)
	})(i)
}  // 55555
```
```
for(var i = 0; i< 5; i++){
    setTimeout(function(i){
           console.log(i)
	}(i),i*1000)
}  // 01234
```
```
for(var i = 0; i< 5; i++){
    setTimeout(function(i){
           console.log(i)
	},i*1000)
}  // 5个undefined
```
```
for(var i = 0; i< 5; i++){
	let j = i;
    setTimeout(function timer(){
           console.log(j)
	},j*1000)
}  // 0, 1, 2, 3, 4
```
```
for(let i = 0; i< 5; i++){
    setTimeout(function timer(){
           console.log(i)
	},i*1000)
}  // 0, 1, 2, 3, 4
```
