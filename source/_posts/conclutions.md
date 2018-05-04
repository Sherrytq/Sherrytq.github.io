---
title: 总结
category: front-end
tag: [js, css] 
archive: front-end
---
###  代码规范
>参考链接： [https://github.com/ecomfe/spec](https://github.com/ecomfe/spec)

### `typeof` and `instanceof`
`typeof`  undefined boolean number string object function、symbol
 
`instanceof` 实例跟构造函数的对应

###  引用类型 and 值类型
* 引用类型 ： Function Object Array 
* 值类型： Boolean String Number Undefined Null 
###  原型和原型链
>对于这个问题，可以从下面这几个要点来理解和回答，下面几条必须记住并且理解  
* 所有的引用类型（数组、对象、函数），都具有对象特性，即可自由扩展属性（null除外）
* 所有的引用类型（数组、对象、函数），都有一个__proto__属性，属性值是一个普通的对象
* 所有的函数，都有一个prototype属性，属性值也是一个普通的对象
* 所有的引用类型（数组、对象、函数），__proto__属性值指向它的构造函数的prototype属性值...

```
// 构造函数
function Foo(name, age) {
    this.name = name
}
Foo.prototype.alertName = function () {
    console.log(6, this) //6 Foo {name: "zhangsan", printName: ƒ}
    console.log(7,this.name)
}
// 创建示例
var f = new Foo('zhangsan')
f.printName = function () {
  console.log(5, this) //5 Foo {name: "zhangsan", printName: ƒ}
    console.log(8,this.name)
}
// 测试
f.printName()
f.alertName()

// 要点二：__proto__
console.log(1, Foo.__proto__); //1 ƒ () { [native code] }
console.log(2, f.__proto__); //2 {alertName: ƒ, constructor: ƒ}

// 要点三：函数有 prototype
console.log(3, Foo.prototype) //3 {alertName: ƒ, constructor: ƒ}
console.log(4, f.prototype) //4 undefined

// 判断这个属性是不是对象本身的属性hasOwnProperty

// var item
// for (item in f) {
//     // 高级浏览器已经在 for in 中屏蔽了来自原型的属性，但是这里建议大家还是加上这个判断，保证程序的健壮性
//     if (f.hasOwnProperty(item)) {
//         console.log(item)
//     }
// }
// 
console.log(Foo.hasOwnProperty('printName'))
```
原型链的终点： `Object.prototype.__proto__ === null`

###  前端异步的场景  
* 定时 setTimeout setInterval  
* 网络请求，如 Ajax <img>加载

###  圣杯布局和双飞翼布局

[https://juejin.im/entry/5a8868cdf265da4e7e10c133?utm_source=gold_browser_extension](https://juejin.im/entry/5a8868cdf265da4e7e10c133?utm_source=gold_browser_extension "https://juejin.im/entry/5a8868cdf265da4e7e10c133?utm_source=gold_browser_extension")

### `fetch` 请求数据 

### SVN 和 Git 的区别   
 SVN 是每一步操作都离不开服务器，创建分支、提交代码都需要连接服务器。而 Git 就不一样了，你可以在本地创建分支、提交代码，最后再一起 push 到服务器上。因此，Git 拥有 SVN 的所有功能，但是却比 SVN 强大得多。（Git 是 Linux 的创始人 Linus 发明的东西，因此也倍得推崇。）

### 浏览器缓存

![](https://i.imgur.com/jojjnCD.png)

### CommonJS (CJS node.js)
   EcmaScript modules( ESM )
三个步骤 ： 
* 构建：查找，下载，然后把所有文件解析成模块记录。
* 实例化：为所有模块分配内存空间（此刻还没有填充值），然后依照导出、导入语句把模块指向对应的内存地址。这个过程称为链接（Linking）。
* 运行：运行代码，从而把内存空间填充为真实值。

* CJS 同步 使用不同的算法  返回模块实例之前，顺着整颗依赖树去逐一加载、实例化和运行每一个依赖
* ESM 异步 把算法化为多个阶段

## 参考链接
[Web 建站技术中，HTML、HTML5、XHTML、CSS、SQL、JavaScript、PHP、ASP.NET、Web Services 是什么？](https://www.zhihu.com/question/22689579)  
[import、require、export、module.exports 混合详解](https://mp.weixin.qq.com/s/lohBbUsVQyIhKcMMUFRZGg)

