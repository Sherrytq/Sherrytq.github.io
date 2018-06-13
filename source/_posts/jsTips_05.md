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
###   input 输入金额必须是数字
```	
$(".other_num").keypress(function(e) {
	    var keyCode;
	    window.event ? keyCode = e.keyCode :keyCode = e.which;
		var keyStr = String.fromCharCode(keyCode);
        return /\d/.test(keyStr) || keyCode == 8; //firefox 下需要考虑backspace 删除键 keyCode = 8
});
```
>参考链接： [http://www.cnblogs.com/chenwenhao/p/7050019.html](http://www.cnblogs.com/chenwenhao/p/7050019.html "http://www.cnblogs.com/chenwenhao/p/7050019.html")
### js jquery 中 ul li的运用
[http://www.cnblogs.com/weihengblogs/p/3961616.html](http://www.cnblogs.com/weihengblogs/p/3961616.html "http://www.cnblogs.com/weihengblogs/p/3961616.html")

### 禁止在<input>中输入中文
[https://blog.csdn.net/u011199063/article/details/73775443](https://blog.csdn.net/u011199063/article/details/73775443 "https://blog.csdn.net/u011199063/article/details/73775443")

### 倒计时
```
		var t = 6;  
		//显示倒数秒数  
		function showTime(){  
		    t -= 1;  
		    $("#leftTime").html(t+'秒');  
		    if(t==0){  
		        window.location.href="http://guba.eastmoney.com/";  
		    }  
		    // 每秒执行一次,showTime()  
		    setTimeout(showTime,1000);  
		} 

		showTime(); 
``` 

### 更换一段文字中的表情文字
```
function  showface (html) {
      var facearr = ["微笑","大笑","鼓掌","不说了","为什么","哭","不屑","怒","滴汗","拜神","胜利","亏大了","赚大了","牛","俏皮","傲","好困惑","兴奋","赞","不赞","摊手","好逊","失望","加油","困顿","想一下","围观","献花","大便","爱心","心碎","毛估估","成交","财力","护城河","复盘","买入","卖出","满仓","空仓","抄底","看多","看空","加仓","减仓"];
      var re = new RegExp('\\[.+?\\]', "ig");
      html = html.replace(re, function (item) {
          for (var i = 0; i < facearr.length; i++){
            if( "[" + facearr[i] + "]" == item ){
              if( i < 9 ){
                return '<img title="' + facearr[i] + '" src="http://gbres.dfcfw.com/face/emot/emot0' + (i + 1) + '.png" alt="' + item + '">';
              }
              else{
                return '<img title="' + facearr[i] + '" src="http://gbres.dfcfw.com/face/emot/emot' + (i + 1) + '.png" alt="' + item + '">';
              }
              break;
            }
          }
          return item;
        });
        
      return html;
}
```

### 获取网页的meta 和 title
```
        //设置页面title
        var titleSummary = text.TxtLeftta(content,30);
        var title = rewardMoney? '(悬赏金额'+rewardMoney+'元)'+ titleSummary+ '_东方财富问答': titleSummary+ '_东方财富问答';
        $(document).attr('title',title);

        //设置页面description
        // var description = document.querySelector('meta[name="description"]');
        var description = $('meta[name="description"]');
        $(description).attr('content',Question.Content)
```

### js 去重
[https://github.com/mqyqingfeng/Blog/issues/27](https://github.com/mqyqingfeng/Blog/issues/27 "https://github.com/mqyqingfeng/Blog/issues/27")