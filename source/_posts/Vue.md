---
title: Vue
category: front-end
tag: Vue
archive: front-end
---

### 生命周期
![vue生命周期](https://i.imgur.com/xnumWs2.png)

### 常用命令
Vue.js提供了一些常用的内置指令，接下来我们将介绍以下几个内置指令：
* v-if指令
* v-show指令
* v-else指令
* v-for指令
* v-bind指令
* v-on指令

`v-if`是条件渲染指令，它根据表达式的真假来删除和插入元素
`v-show`也是条件渲染指令，和`v-if`指令不同的是，使用`v-show`指令的元素始终会被渲染到HTML，它只是简单地为元素设置CSS的style属性。
`v-else`指令为`v-if`或`v-show`添加一个“else块”。`v-else`元素必须立即跟在`v-if`或`v-show`元素的后面——否则它不能被识别。
`v-for`指令基于一个数组渲染一个列表，它和JavaScript的遍历语法相似：
```
v-for="item in items"
```
items是一个数组，item是当前被遍历的数组元素。
 
`v-bind`指令可以在其名称后面带一个参数，中间放一个冒号隔开，这个参数通常是HTML元素的特性（attribute），例如：`v-bind:class` `v-bind:argument="expression"`
 
`v-on`指令用于给监听DOM事件，它的用语法和`v-bind`是类似的，例如监听`<a>`元素的点击事件:

```
<a v-on:click="doSomething">
```

有两种形式调用方法：绑定一个方法（让事件指向方法的引用），或者使用内联语句。

Vue.js为最常用的两个指令`v-bind`和`v-on`提供了缩写方式。`v-bind`指令可以缩写为一个冒号，`v-on`指令可以缩写为`@`符号。
```
<!--完整语法-->
<a href="javascripit:void(0)" v-bind:class="activeNumber === n + 1 ? 'active' : ''">{{ n + 1 }}</a>
<!--缩写语法-->
<a href="javascripit:void(0)" :class="activeNumber=== n + 1 ? 'active' : ''">{{ n + 1 }}</a>
<!--完整语法-->
<button v-on:click="greet">Greet</button>
<!--缩写语法-->
<button @click="greet">Greet</button>
```

### 组件间通信
在子组件中定义props，可以让父组件的数据传递下来
今天我们将着重介绍slot和父子组件之间的访问和通信，slot是一个非常有用的东西，它相当于一个内容插槽，它是我们重用组件的基础。Vue的事件系统独立于原生的DOM事件，它用于组件之间的通信
本文的主要内容如下：
* 组件的编译作用域
* 在组件template中使用<slot>标签作为内容插槽
* 使用$children, $refs, $parent 实现父子组件之间的实例访问
* 在子组件中，使用$dispatch向父组件派发事件；在父组件中，使用$broadcast向子组件传播事件
* 结合这些基础知识，我们一步一步实现一个CURD的示例

有时候我们需要父组件访问子组件，子组件访问父组件，或者是子组件访问根组件。
针对这几种情况，Vue.js都提供了相应的API：
* 父组件访问子组件：使用$children或$refs
* 子组件访问父组件：使用$parent
* 子组件访问根组件：使用$root

注意：尽管可以访问父链上任意的实例，不过子组件应当避免直接依赖父组件的数据，尽量显式地使用 props 传递数据。另外，在子组件中修改父组件的状态是非常糟糕的做法，因为： 
* 这让父组件与子组件紧密地耦合； 
* 只看父组件，很难理解父组件的状态。因为它可能被任意子组件修改！理想情况下，只有组件自己能修改它的状态。


有时候我们希望触发父组件的某个事件时，可以通知到子组件；触发子组件的某个事件时，可以通知到父组件
Vue 实例实现了一个自定义事件接口，用于在组件树中通信。这个事件系统独立于原生 DOM 事件，用法也不同。
每个 Vue 实例都是一个事件触发器：
* 使用 $on() 监听事件；
* 使用 $emit() 在它上面触发事件；
* 使用 $dispatch() 派发事件，事件沿着父链冒泡；
* 使用 $broadcast() 广播事件，事件向下传导给所有的后代。

### 组件的创建与注册
Vue.js的组件的使用有3个步骤：创建组件构造器、注册组件和使用组件。
![组件的创建与注册](https://i.imgur.com/0REImoZ.png)

我们用以下几个步骤来理解组件的创建和注册：
1. Vue.extend()是Vue构造器的扩展，调用Vue.extend()创建的是一个组件构造器。 
2. Vue.extend()构造器有一个选项对象，选项对象的template属性用于定义组件要渲染的HTML。 
3. 使用Vue.component()注册组件时，需要提供2个参数，第1个参数时组件的标签，第2个参数是组件构造器。 
4. 组件应该挂载到某个Vue实例下，否则它不会生效。

Vue.js规定：在定义组件的选项时，data和el选项必须使用函数。
组件实例的作用域是孤立的。这意味着不能并且不应该在子组件的模板内直接引用父组件的数据。可以使用 props 把数据传给子组件。

注意：在子组件中定义prop时，使用了camelCase命名法。由于HTML特性不区分大小写，camelCase的prop用于特性时，需要转为 kebab-case（短横线隔开）。例如，在prop中定义的myName，在用作特性时需要转换为my-name。

`<child-component v-bind:子组件prop="父组件数据属性"></child-component>`

`prop`默认是单向绑定：当父组件的属性变化时，将传导给子组件，但是反过来不会。这是为了防止子组件无意修改了父组件的状态

* 双向绑定
可以使用`.sync`显式地指定双向绑定，这使得子组件的数据修改会回传给父组件。
`<my-component v-bind:my-name.sync="name" v-bind:my-age.sync="age"></my-component>`
* 单次绑定
可以使用`.once`显式地指定单次绑定，单次绑定在建立之后不会同步之后的变化，这意味着即使父组件修改了数据，也不会传导给子组件。
`<my-component v-bind:my-name.once="name" v-bind:my-age.once="age"></my-component>`

Vue.js组件的API来源于三部分——prop，slot和事件。
* prop 允许外部环境传递数据给组件；
* 事件 允许组件触发外部环境的 action；
* slot 允许外部环境插入内容到组件的视图结构内。

### 深拷贝
```
initItemForUpdate: function(p) {
    var c = c || {};
    for (var i in p) {
        // 属性i是否为p对象的自有属性
        if (p.hasOwnProperty(i)) {
            if (typeof p[i] === 'object') {
                c[i] = Array.isArray(p[i]) ? [] : {}
                deepCopy(p[i], c[i])
            } else {
                // 属性是基础类型时，直接拷贝
                c[i] = p[i]
            }
        }
    }
    return c;
}
```

## 参考链接  
[Vue 官方说明](https://cn.vuejs.org/v2/guide/syntax.html)  
[Vue 60分钟快速入门](http://www.cnblogs.com/keepfool/p/5619070.html)