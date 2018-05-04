---
title: Interview  
category: front-end   
tag: Interview          
archive: front-end  
---

### 原型链 
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

[https://mp.weixin.qq.com/s/USeD-bnuSPXX8p2HnIrzqQ](https://mp.weixin.qq.com/s/USeD-bnuSPXX8p2HnIrzqQ "https://mp.weixin.qq.com/s/USeD-bnuSPXX8p2HnIrzqQ")

[https://mp.weixin.qq.com/s/R4msIJru54oowBG9pR3dHw](https://mp.weixin.qq.com/s/R4msIJru54oowBG9pR3dHw "https://mp.weixin.qq.com/s/R4msIJru54oowBG9pR3dHw")
![](https://i.imgur.com/ZwZaGfA.png)

### Promise 

[https://mp.weixin.qq.com/s/nrekW0wPeXQASc3eWK_7Vw](https://mp.weixin.qq.com/s/nrekW0wPeXQASc3eWK_7Vw "https://mp.weixin.qq.com/s/nrekW0wPeXQASc3eWK_7Vw")

### 关于网络请求的面试题总结

[https://mp.weixin.qq.com/s/_cfUXkUJJHhih1WkHFBAMg](https://mp.weixin.qq.com/s/_cfUXkUJJHhih1WkHFBAMg "https://mp.weixin.qq.com/s/_cfUXkUJJHhih1WkHFBAMg")

### 关于客户端存储的前端面试题总结
[https://mp.weixin.qq.com/s/efJ9r7VyuUKBLADKY-he-Q](https://mp.weixin.qq.com/s/efJ9r7VyuUKBLADKY-he-Q "https://mp.weixin.qq.com/s/efJ9r7VyuUKBLADKY-he-Q")

### 关于数字的前端面试题
[https://mp.weixin.qq.com/s/-xtFAUmWbIOvjgpgS0-EmQ](https://mp.weixin.qq.com/s/-xtFAUmWbIOvjgpgS0-EmQ "https://mp.weixin.qq.com/s/-xtFAUmWbIOvjgpgS0-EmQ")

### 关于数据类型转换的面试题总结
[https://mp.weixin.qq.com/s/VoPCr4PgH_bRsOi907BzJg](https://mp.weixin.qq.com/s/VoPCr4PgH_bRsOi907BzJg "https://mp.weixin.qq.com/s/VoPCr4PgH_bRsOi907BzJg")