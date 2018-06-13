---
title: Handlebars  
category: front-end   
tag: Handlebars           
archive: front-end  
---
### 基本知识

Handlebars.js是一款基于Jquery的插件，以json对象为数据源，支持逻辑判断、循环等操作，同时具有非常好的扩展性，体积60KB左右， 是一款js模版引擎。
```
//原生方法
var source = document.getElementById('#tpl').innerHTML;
//预编译模板
var template = Handlebars.compile(source);
//模拟json数据
var context = { name: "zhaoshuai", content: "learn Handlebars"};
//匹配json内容
var html = template(context);
//输入模板
$(body).html(html);
```
### `registerHelper` 可以自定义函数
```
{{#each student}}
    <tr>
      <td>{{name}}</td>
      <td>{{sex}}</td>
      <td>{{age}}</td>
      {{#compare age 20}}
        <td>{{homePage}}</td>
      {{else}}
        <td>{{{homePage}}}</td>
      {{/compare}}
    </tr> 
{{/each}}
```
```
Handlebars.registerHelper("compare",function(v1,v2,options){
	  //判断v1是否比v2大
	  if(v1>v2){
	    //继续执行
	    return options.fn(this);
	  }else{
	    //执行else部分
	    return options.inverse(this);
	  }
});
``` 
### 小节
`Handlebars` 
* 核心： 样式和逻辑进行分离，先将样式渲染到页面，才可能获取到dom 元素，然后才能进行dom 操作，
* 优点： 将样式和逻辑进行了分离，很像react的思想，使项目的结构更加清楚，也很适合团队合作
* 缺点： 
> * 组件间有关联时，尤其是遇到请求数据的情况，很难确认哪个组件先获取数据，先进行渲染  
> * 方法：  
>先进行dom 元素渲染，在插入数据  
>运用返回函数，在第二的请求函数中调用第一个组件的函数
```
	 stock.getSingleCodeName(stockCode,function(stockName){
       	$("#backTobar").html('返回'+stockName+'吧>>') ;
             return false;  
     });   
```
（2） 组件中请求数据后需要进行dom操作


## 参考链接
[Handlebars.js 模板引擎](http://caibaojian.com/handlebars-js.html)