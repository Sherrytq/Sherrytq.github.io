---
title: JSTIPS_01
category: front-end
tag: js
archive: frontEnd
---


### 1. 事件的捕获和冒泡
除了IE 之外先捕获 -> 当前节点事件 -> 后冒泡

```
<div id="parent" onclick="alert(99)">测试不阻止事件冒泡
     <button id="child" onclick="alert(4)">我是内部div</button>
</div>
//js
document.body.addEventListener("click",function(event){
    alert("event bubble");
},false);
document.body.addEventListener("click",function(event){
    alert("event catch");
 },true);
```

点击parent ： event catch -> 99 ->event bubble

点击child:       event catch -> 4 -> 99 ->event bubble

### 2. 原型和原型链
```
function Dog(breed, name){
 this.breed = breed,
 this.name = name
}
Dog.prototype.describe = function() {
 console.log(`${this.name} is a ${this.breed}`)
}
const rusty = new Dog('Beagle', 'Rusty');

/* .prototype property points to an object which has constructor and attached 
properties to be inherited by objects created by this constructor. */
console.log(Dog.prototype)  // { describe: ƒ , constructor: ƒ }

/* Object created from Dog constructor function */
console.log(rusty)   //  { breed: "Beagle", name: "Rusty" }
/* Object inherited properties from constructor function's prototype */
console.log(rusty.describe())   // "Rusty is a Beagle"
/* .__proto__ property points to the .prototype property of the constructor function */ 
console.log(rusty.__proto__)    // { describe: ƒ , constructor: ƒ }
/* .constructor property points to the constructor of the object */
console.log(rusty.constructor)  // ƒ Dog(breed, name) { ... }
```
### 3. [动态加载图片取不到宽高](https://segmentfault.com/q/101000000435521)
``` 
function loadImage(url, callback) {    
    var img = new Image(); //创建一个Image对象，实现图片的预下载     
    img.onload = function(){
        img.onload =null;
        callback(img);
    }
    img.src = url; 
}
```
### 4. [遍历子节点的方法](https://segmentfault.com/a/1190000010661082)

### 5. 数组的处理方法是否改变原数组 
  slice concat join 不会改变
```
var source = [1,2,3,4,5]
//原数组不会改变
source.slice(1,3); // 返回[2,3]
source.concat([6,7]) //返回[1,2,3,4,5,6,7]
source.join('-') //返回 1-2-3-4-5
//原数组会变
source.splice(1,3) //返回 [2,3,4]
source.pop();
source.push();
source;shift();
source.unshift();
source.reverse();
```
### 6. h5 选中元素
 querySelector（获得第一个满足条件的元素  
 querySelectorAll ( 这个出来的是一个数组）
### 7. 原生的li 点击事件
``` 
for(var i = 0; i< reloadDiv.length ;i++){
    index = i;
    reloadDiv[index].onclick = function(){
      _this.loadimg();
      return false;
     };
 }
```
### 8. URL 地址 参数获取介绍： 
```
var url = http://www.jianshu.com/writer#/notebooks/18682777/notes/20130528/preview
//设置或获取对象指定的文件名或路径。
alert(window.location.pathname);// "/writer" 
//设置或获取整个 URL 为字符串。
alert(window.location.href);// "http://www.jianshu.com/writer#/notebooks/18682777/notes/20130528/preview"
//设置或获取与 URL 关联的端口号码。
alert(window.location.port);//"" 
//设置或获取 URL 的协议部分。
alert(window.location.protocol);//"http:" 
//设置或获取 href 属性中在井号“#”后面的分段。
alert(window.location.hash);//"#/notebooks/18682777/notes/20130528/preview" 
//设置或获取 location 或 URL 的 hostname 和 port 号码。
alert(window.location.host);//"www.jianshu.com" 
//设置或获取 href 属性中跟在问号后面的部分。
alert(window.location.search);//"" 
```
### 9. [jquery on 和 off 事件](http://www.jb51.net/article/95723.htm)
一个Button 键可能会被调用很多次，可以off 取消之前的click 事件
### 10. [详解clientHeight、offsetHeight、scrollHeight](http://blog.csdn.net/woxueliuyun/article/details/8638427)
clientHeight: 内容可视区域的高度  
offsetHeight: IE、Opera 认为 offsetHeight = clientHeight + 滚动条 + 边框。  
NS、FF 认为 offsetHeight 是网页内容实际高度，可以小于 clientHeight。
scrollHeight: IE、Opera 认为 scrollHeight 是网页内容实际高度，可以小于 clientHeight。  
NS、FF 认为 scrollHeight 是网页内容高度，不过最小值是 clientHeight
>chrome浏览器下 元素
offsetHeight = padding + border + height；
clientHeight = padding + height -水平滚动条的高度；
scrollHeight >= clientHeight；
offsetLeft = 元素border左上角到画布原点的距离 或 到offsetParent的border box顶部的距离。
### 11. [ES6 的相关知识](https://75team.com/post/5-javascript-%E2%80%9Cbad%E2%80%9D-parts-that-are-fixed-in-es6.html)
>**增加的新功能：**
箭头操作符 () => {}
类的支持 class
增强的对象字面量
可以在对象字面量里面定义原型
定义方法可以不用function关键字
直接调用父类方法
字符串模板 :`${}`
解构
let const 
### 12. 上传资源的方法 post put patch 
>POST方法用来创建一个子资源，如 /api/users，会在users下面创建一个user，如users/1
POST方法不是幂等的，多次执行，将导致多条相同的用户被创建（users/1，users/2 ...而这些用户除了自增长id外有着相同的数据，除非你的系统实现了额外的数据唯一性检查）
PUT方法用来创建一个URI已知的资源，或对已知资源进行完全替换，比如users/1，
PUT方法一般会用来更新一个已知资源，除非在创建前，你完全知道自己要创建的对象的URI。
PATCH方法是新引入的，是对PUT方法的补充，用来对已知资源进行局部更新
get 和 post比较常见  GET请求将提交的数据放置在HTTP请求协议头中
POST提交的数据则放在实体数据中
简单来说： 
get -> list
post -> create
patch -> update
