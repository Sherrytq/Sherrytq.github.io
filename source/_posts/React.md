---
title: React
category: front-end
tag: React
archive: frontEnd
---
1.  React 知识
React 的核心思想是：封装组件。
各个组件维护自己的状态和 UI，当状态变更，自动重新渲染整个组件。
基于这种方式的一个直观感受就是我们不再需要不厌其烦地来回查找某个 DOM 元素，然后操作 DOM 去更改 UI。

2. React 大体包含下面这些概念：
- **组件**
- **JSX**
- **Virtual DOM** 
- **Data Flow**

3. 组件的生命周期
![image.png](http://upload-images.jianshu.io/upload_images/8952934-6183b3ea3c3749c3.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![流](https://i.imgur.com/HBH9ySZ.png)

4. [React-router](https://segmentfault.com/a/1190000004075348)

5. react 基本知识
![](https://i.imgur.com/EZnakf8.png)  

![](https://i.imgur.com/0qwoWvM.png)
 
![](https://i.imgur.com/ZH0TlBZ.png)

![](https://i.imgur.com/Nm4Ger0.png)

![](https://i.imgur.com/EzXrPJv.png)

![](https://i.imgur.com/SLit5kb.png)

![](https://i.imgur.com/HQSnC5O.png)

6. 组件间通信
React中组件通信的三种方法：
* 使用props，构建通信链
* 在组件初始化的时候，保存组件的句柄，在其它组件中，使用此句柄达到直接访问组件的目的，完成通信
* 使用PubSub模式

第1种方式，在组件嵌套较深时，显示不适用。  
第2种在组件很多时，也得定义维护很多变量。  
PubSub模式有助于解藕和代码组织，在React的组件通信时，推荐使用此方法。  

参考链接：   
[react 组件间通信](http://www.alloyteam.com/2015/07/react-zu-jian-jian-tong-xin/)

7. React中的state说明
#### 哪些组件应该有 State？  
大部分组件的工作应该是从 props 里取数据并渲染出来。但是，有时需要对用户输入、服务器请求或者时间变化等作出响应，这时才需要使用 State。  
尝试把尽可能多的组件无状态化。 这样做能隔离 state，把它放到最合理的地方，也能减少冗余，同时易于解释程序运作过程。常用的模式是创建多个只负责渲染数据的无状态（stateless）组件，在它们的上层创建一个有状态（stateful）组件并把它的状态通过 props 传给子级。这个有状态的组件封装了所有用户的交互逻辑，而这些无状态组件则负责声明式地渲染数据。
#### 哪些 应该 作为 State？  
State 应该包括那些可能被组件的事件处理器改变并触发用户界面更新的数据。 真实的应用中这种数据一般都很小且能被 JSON 序列化。当创建一个状态化的组件时，想象一下表示它的状态最少需要哪些数据，并只把这些数据存入 this.state。在 render() 里再根据 state 来计算你需要的其它数据。你会发现以这种方式思考和开发程序最终往往是正确的，因为如果在 state 里添加冗余数据或计算所得数据，需要你经常手动保持数据同步，不能让 React 来帮你处理。

#### 哪些 不应该 作为 State？
this.state 应该仅包括能表示用户界面状态所需的最少数据。因此，它不应该包括：
* 计算所得数据： 不要担心根据 state 来预先计算数据 —— 把所有的计算都放到render() 里更容易保证用户界面和数据的一致性。例如，在 state 里有一个数组（listItems），我们要把数组长度渲染成字符串， 直接在 render() 里使用this.state.listItems.length + ' list items' 比把它放到 state 里好的多。
* React 组件： 在 render() 里使用当前 props 和 state 来创建它。
* 基于 props 的重复数据： 尽可能使用 props 来作为惟一数据来源。把 props 保存到 state 的一个有效的场景是需要知道它以前值的时候，因为未来的 props 可能会变化。


8. redux
解决了react中处理state的问题
三大原则： 
单一数据源
整个应用的 state 被储存在一棵 object tree 中，并且这个 object tree 只存在于唯一一个 store 中。
State 是只读的
惟一改变 state 的方法就是触发 action，action 是一个用于描述已发生事件的普通对象。
使用纯函数来执行修改
为了描述 action 如何改变 state tree ，你需要编写 reducers。Reducer 只是一些纯函数，它接收先前的 state 和 action，并返回新的 state。

* Action  
Action 是把数据从应用（译者注：这里之所以不叫 view 是因为这些数据有可能是服务器响应，用户输入或其它非 view 的数据 ）传到 store 的有效载荷。它是 store 数据的唯一来源。一般来说你会通过store.dispatch() 将 action 传到 store。
* Reduce   
Action 只是描述了有事情发生了这一事实，并没有指明应用如何更新 state。而这正是 reducer 要做的事情。
 现在我们已经确定了 state 对象的结构，就可以开始开发 reducer。reducer 就是一个纯函数，接收旧的 state 和 action，返回新的 state。

![action](https://i.imgur.com/nr5cyQ5.png)
`combineReducers()` 所做的只是生成一个函数，这个函数来调用你的一系列 reducer，每个 reducer 根据它们的 key 来筛选出 state 中的一部分数据并处理，然后这个生成的函数再将所有 reducer 的结果合并成一个大的对象

* Store
![store](https://i.imgur.com/pCc8jKk.png)




## 参考链接
[阮一峰 react 入门](http://www.ruanyifeng.com/blog/2015/03/react.html)





