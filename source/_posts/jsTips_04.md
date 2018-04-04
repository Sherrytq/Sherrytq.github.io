---
title: JSTIPS_04
category: front-end
tag: js
archive: frontEnd
---

1. 为什么要使用 addEventListener?
addEventListener 是 W3C DOM 规范中提供的注册事件监听器的方法。它的优点包括：  
* 它允许给一个事件注册多个 listener。当存在其他的库时，使用 DHTML 库或者 Mozilla extensions 不会出现问题。
* 它提供了一种更精细的手段控制 listener 的触发阶段。（即可以选择捕获或者冒泡）。
* 它对任何 DOM 元素都是有效的，而不仅仅只对 HTML 元素有效。

2. `===` 与 `==`
![`===` 和 `==`](https://i.imgur.com/z4JOisU.png) 
 
![](https://i.imgur.com/LAkOElS.png) 
 
![](https://i.imgur.com/UZXi3Ym.png)

3. 类型判断
```
typeof b
c.constructor
d instanceof "number"
type(f)
```
![](https://i.imgur.com/zhm7Hq3.png)  

![](https://i.imgur.com/YJpd6TS.png)

![](https://i.imgur.com/SzREjsE.png)

```
typeof 'a' => "string"
Object.prototype.toString.call('a) => [object String]
constructor: 
function getConstructiorName(obj) {
return obj && obj.constructor && obj.constructor.toString().match(/function\s*([^(]*)/)[1];
}
getConstructiorName([]) === "Array"; // true
'null' instanceof String => false
```
 4. [动态加载图片取不到宽高](https://segmentfault.com/q/1010000004355214)

 5. [遍历子节点的方法](https://segmentfault.com/a/1190000010661082)

6. 对象转换成数组的方法
``` 
Array.from(obj)  
[].slice.call(obj)
```

7. `callee` 和 `caller` 的作用
  ![](https://i.imgur.com/FD9OlaK.png)

8. 一次完整的http 事务是怎样的过程
   ![http 请求](https://i.imgur.com/bBoKLxM.png)

输入网址到出现页面的过程

* 向dns服务器请求网址的IP地址
* 通过80端口向目标IP地址发送http请求
* 目标服务器接受请求，将请求内容封装在http响应报文中并发送
* 接受http响应报文并解析，然后在浏览器上显示出来
![渲染](https://i.imgur.com/D0UlMtb.png)

9. cookie 
第一个选项是过期时间（expires），指定了 cookie 何时不会再被发送至服务器，随后浏览器将删除该 cookie。该选项的值是一个 Wdy, DD-Mon-YYYY HH:MM:SS GMT 日期格式的值，

![image.png](https://upload-images.jianshu.io/upload_images/8952934-a92b7da727c74209.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


下一个选项是 domain，指定了 cookie 将要被发送至哪个或哪些域中。默认情况下，domain会被设置为创建该 cookie 的页面所在的域名，所以当给相同域名发送请求时该 cookie 会被发送至服务器。

![image.png](https://upload-images.jianshu.io/upload_images/8952934-38dfabd2719bc995.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![image.png](https://upload-images.jianshu.io/upload_images/8952934-d6095a40a6c91957.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

10. `childNodes` 与  `children`
`childNodes`：它是标准属性，它返回指定元素的子元素集合，包括HTML节点，所有属性，文本节点。
 `children`：非标准属性，它返回指定元素的子元素集合。
但它只返回HTML节点，甚至不返回文本节点，虽然不是标准的DOM属性，但它和innerHTML方法一样，得到了几乎所有浏览器的支持。



