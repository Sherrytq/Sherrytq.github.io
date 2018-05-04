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

## 参考链接
[Handlebars.js 模板引擎](http://caibaojian.com/handlebars-js.html)