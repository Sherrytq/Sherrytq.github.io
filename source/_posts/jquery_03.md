---
title: jQuery 源码分析
category: front-end
tag: [js,jquery]
archive: front-end
---
## The Write Less, Do More 

### 整体架构 
1. jQuery 2.1.1 源码结构
```
;(function(global, factory) {
    factory(global);
}(typeof window !== "undefined" ? window : this, function(window, noGlobal) {
    var jQuery = function( selector, context ) {
		return new jQuery.fn.init( selector, context );
	};
	jQuery.fn = jQuery.prototype = {};
	// 核心方法
	// 回调系统
	// 异步队列
	// 数据缓存
	// 队列操作
	// 选择器引
	// 属性操作
	// 节点遍历
	// 文档处理
	// 样式操作
	// 属性操作
	// 事件体系
	// AJAX交互
	// 动画引擎
	return jQuery;
}));
```
2. jq的模块依赖网

![](https://i.imgur.com/sjgZyQ5.png)

### 立即调用表达式
任何库与框架设计的第一个要点就是解决命名空间与变量污染的问题。jQuery就是利用了JavaScript函数作用域的特性，采用立即调用表达式包裹了自身的方法来解决这个问题。
```
//写法1 
(function(window, factory) {
    factory(window)
}(this, function() {
    return function() {
       //jQuery的调用
    }
}))
//写法2
var factory = function(){
    return function(){
        //执行方法
    }
}
var jQuery = factory();
//写法3
(function(window, undefined) {
    var jQuery = function() {}
    // ...
    window.jQuery = window.$ = jQuery;
})(window);
```

全局变量是魔鬼, 匿名函数可以有效的保证在页面上写入JavaScript，而不会造成全局变量的污染，通过小括号，让其加载的时候立即初始化，这样就形成了一个单例模式的效果从而只会执行一次。

### jq的类数据对象结构
通过对象键值对的关系保存着属性，原型保存着方法
```
var aQuery = function(selector) {
    //强制为对象
	if (!(this instanceof aQuery)) {
		return new aQuery(selector);
	}
	var elem = document.getElementById(/[^#].*/.exec(selector)[0]);
	this.length = 1;
	this[0] = elem;
	this.context = document;
	this.selector = selector;
	this.get = function(num) {
		return this[num];
	}
	return this;
}
```
### jQuery中ready与load事件
jQuery有3种针对文档加载的方法
```
$(document).ready(function() {
    // ...代码...
})
//document ready 简写
$(function() {
    // ...代码...
})
$(document).load(function() {
    // ...代码...
})
```
`ready先执行，load后执行。`

DOM文档加载的步骤：
要想理解为什么ready先执行，load后执行就要先了解下DOM文档加载的步骤：
```
(1) 解析HTML结构。
(2) 加载外部脚本和样式表文件。
(3) 解析并执行脚本代码。
(4) 构造HTML DOM模型。//ready
(5) 加载图片等外部文件。
(6) 页面加载完毕。//load
```
### jq多库共存处理（无冲突处理） 
`noConflict` 函数

### init 构造图
![](https://i.imgur.com/Bjjiqp8.png)
```
ajQuery.fn = ajQuery.prototype = {
        name: 'aaron',
        init: function(selector) {
               this.selector = selector;
               return this;
        },
        constructor: ajQuery
}
ajQuery.fn.init.prototype = ajQuery.fn
```