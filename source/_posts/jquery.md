---
title: Jquery  
category: front-end   
tag: [js, jquery]            
archive: front-end  
---

### 兼容性

这里需要注意 jQuery 分 2 个系列版本 1.x 与 2.x，主要的区别在于 2.x 不再兼容 IE6、7、8浏览器，这样做的目的是为了兼容移动端开发。

抛开jQuery，如果要获取文档中所有的元素，通过document.getElementsByTagName()中传递"*"同样可以获取到

不难发现，id、class、tag都可以通过原生的方法获取到对应的节点，但是我们还需要考虑一个兼容性的问题，我这里顺便提及一下，比如:

IE会将注释节点实现为元素，所以在IE中调用getElementsByTagName里面会包含注释节点，这个通常是不应该的
getElementById的参数在IE8及较低的版本不区分大小写
IE7及较低的版本中，表单元素中，如果表单A的name属性名用了另一个元素B的ID名并且A在B之前，那么getElementById会选中A
IE8及较低的版本，浏览器不支持getElementsByClassName


### 选择器

![层级选择器](https://i.imgur.com/F2ojRUv.png)

![筛选选择器](https://i.imgur.com/XqL9Uqf.png)
* 注意事项：
:eq(), :lt(), :gt(), :even, :odd 用来筛选他们前面的匹配表达式的集合元素，根据之前匹配的元素在进一步筛选，注意jQuery合集都是从0开始索引
  gt是一个段落筛选，从指定索引的下一个开始，gt(1) 实际从2开始
![内容筛选选择器](https://i.imgur.com/bzCHRXJ.png)
* 注意事项：
:contains与:has都有查找的意思，但是contains查找包含“指定文本”的元素，has查找包含“指定元素”的元素
如果:contains匹配的文本包含在元素的子元素中，同样认为是符合条件的。
:parent与:empty是相反的，两者所涉及的子元素，包括文本节点
![可见性筛选选择器](https://i.imgur.com/8nDN5wV.png)

* 我们有几种方式可以隐藏一个元素：
CSS display的值是none。
type="hidden"的表单元素。
宽度和高度都显式设置为0。
一个祖先元素是隐藏的，该元素是不会在页面上显示
CSS visibility的值是hidden
CSS opacity的指是0

![属性筛选选择器](https://i.imgur.com/w8cC8fD.png)

![子元素筛选选择器](https://i.imgur.com/YHtUz5u.png)
注意事项：

:first只匹配一个单独的元素，但是:first-child选择器可以匹配多个：即为每个父级元素匹配第一个子元素。这相当于:nth-child(1)
:last 只匹配一个单独的元素， :last-child 选择器可以匹配多个元素：即，为每个父级元素匹配最后一个子元素
如果子元素只有一个的话，:first-child与:last-child是同一个
 :only-child匹配某个元素是父元素中唯一的子元素，就是说当前子元素是父元素中唯一的元素，则匹配
jQuery实现:nth-child(n)是严格来自CSS规范，所以n值是“索引”，也就是说，从1开始计数，:nth-child(index)从1开始的，而eq(index)是从0开始的
nth-child(n) 与 :nth-last-child(n) 的区别前者是从前往后计算，后者从后往前计算

![表单元素选择器](https://i.imgur.com/OTW5asM.png)


### jq 中的 `this`

`this`，表示当前的上下文对象是一个html对象，可以调用html对象所拥有的属性和方法。
`$(this)`,代表的上下文对象是一个jquery的上下文对象，可以调用jQuery的方法和属性值。


### .html(),.text()和.val()的差异总结：  

* .html(),.text(),.val()三种方法都是用来读取选定元素的内容；只不过.html()是用来读取元素的html内容（包括html标签），.text()用来读取元素的纯文本内容，包括其后代元素，.val()是用来读取表单元素的"value"值。其中.html()和.text()方法不能使用在表单元素上,而.val()只能使用在表单元素上；另外.html()方法使用在多个元素上时，只读取第一个元素；.val()方法和.html()相同，如果其应用在多个元素上时，只能读取第一个表单元素的"value"值，但是.text()和他们不一样，如果.text()应用在多个元素上时，将会读取所有选中元素的文本内容。
* .html(htmlString),.text(textString)和.val(value)三种方法都是用来替换选中元素的内容，如果三个方法同时运用在多个元素上时，那么将会替换所有选中元素的内容。
* .html(),.text(),.val()都可以使用回调函数的返回值来动态的改变多个元素的内容。


### jQuery的属性与样式之.css()与.addClass()设置样式的区别
对于样式的设置，我们学了addClass与css方法，那么两者之间有什么区别？

可维护性：

.addClass()的本质是通过定义个class类的样式规则，给元素添加一个或多个类。css方法是通过JavaScript大量代码进行改变元素的样式

通过.addClass()我们可以批量的给相同的元素设置统一规则，变动起来比较方便，可以统一修改删除。如果通过.css()方法就需要指定每一个元素是一一的修改，日后维护也要一一的修改，比较麻烦

灵活性：

通过.css()方式可以很容易动态的去改变一个样式的属性，不需要在去繁琐的定义个class类的规则。一般来说在不确定开始布局规则，通过动态生成的HTML代码结构中，都是通过.css()方法处理的

样式值：

.addClass()本质只是针对class的类的增加删除，不能获取到指定样式的属性的值，.css()可以获取到指定的样式值。

样式的优先级：

css的样式是有优先级的，当外部样式、内部样式和内联样式同一样式规则同时应用于同一个元素的时候，优先级如下

外部样式 < 内部样式 < 内联样式
.addClass()方法是通过增加class名的方式，那么这个样式是在外部文件或者内部样式中先定义好的，等到需要的时候在附加到元素上
通过.css()方法处理的是内联样式，直接通过元素的style属性附加到元素上的
通过.css方法设置的样式属性优先级要高于.addClass方法
总结：

.addClass与.css方法各有利弊，一般是静态的结构，都确定了布局的规则，可以用addClass的方法，增加统一的类规则
如果是动态的HTML结构，在不确定规则，或者经常变化的情况下，一般多考虑.css()方式


### DOM节点删除之empty和remove区别
要用到移除指定元素的时候，jQuery提供了empty()与remove([expr])二个方法，两个都是删除元素，但是两者还是有区别

empty方法

严格地讲，empty()方法并不是删除节点，而是清空节点，它能清空元素中的所有后代节点
empty不能删除自己本身这个节点
remove方法

该节点与该节点所包含的所有后代节点将同时被删除
提供传递一个筛选的表达式，删除指定合集中的元素


### DOM节点删除之detach()和remove()区别
JQuery是一个很大强的工具库，在工作开发中，有些方法因为不常用到，或是没有注意到而被我们忽略。

remove()和detach()可能就是其中的一个，可能remove()我们用得比较多，而detach()就可能会很少了

 通过一张对比表来解释2个方法之间的不同
![](https://i.imgur.com/STH7sr4.png)

remove：移除节点

无参数，移除自身整个节点以及该节点的内部的所有节点，包括节点上事件与数据
有参数，移除筛选出的节点以及该节点的内部的所有节点，包括节点上事件与数据
detach：移除节点

移除的处理与remove一致
与remove()不同的是，所有绑定的事件、附加的数据等都会保留下来
例如：$("p").detach()这一句会移除对象，仅仅是显示效果没有了。但是内存中还是存在的。当你append之后，又重新回到了文档流中。就又显示出来了。
具体可以参考右边的代码区域的对比


### .parents()和.closest()是有点相似的，都是往上遍历祖辈元素，但是两者还是有区别的，否则就没有存在的意义了

起始位置不同：.closest开始于当前元素 .parents开始于父元素
遍历的目标不同：.closest要找到指定的目标，.parents遍历到文档根元素，closest向上查找，直到找到一个匹配的就停止查找，parents一直查找到根元素，并将匹配的元素加入集合
结果不同：.closest返回的是包含零个或一个元素的jquery对象，parents返回的是包含零个或一个或多个元素的jquery对象


### mouseenter事件和mouseover的区别

关键点就是：冒泡的方式处理问题
简单的例子：

mouseover为例：
```
<div class="aaron2">
    <p>鼠标离开此区域触发mouseleave事件</p>
</div>
```
如果在p元素与div元素都绑定mouseover事件，鼠标在离开p元素，但是没有离开div元素的时候，触发的结果:

p元素响应事件
div元素响应事件
这里的问题是div为什么会被触发？ 原因就是事件冒泡的问题，p元素触发了mouseover，他会一直往上找父元素上的mouseover事件，如果父元素有mouseover事件就会被触发

所以在这种情况下面，jQuery推荐我们使用 mouseenter事件

mouseenter事件只会在绑定它的元素上被调用，而不会在后代节点上被触发

这就是最本质的区别，具体的对应可以参考右边的案例：


### trigger触发浏览器事件与自定义事件区别？

自定义事件对象，是jQuery模拟原生实现的
自定义事件可以传递参数

triggerHandler与trigger的用法是一样的，重点看不同之处：

triggerHandler不会触发浏览器的默认行为，.triggerHandler( "submit" )将不会调用表单上的.submit()
.trigger() 会影响所有与 jQuery 对象相匹配的元素，而 .triggerHandler() 仅影响第一个匹配到的元素
使用 .triggerHandler() 触发的事件，并不会在 DOM 树中向上冒泡。 如果它们不是由目标元素直接触发的，那么它就不会进行任何处理
与普通的方法返回 jQuery 对象(这样就能够使用链式用法)相反，.triggerHandler() 返回最后一个处理的事件的返回值。如果没有触发任何事件，会返回 undefined


### 添加函数
```

(function($){
  $.fn.extend({
  	'focusColor': function(newColor){
        var oldColor = $(this).css('background-color');
        $(this).hover(function(){
        	$(this).css(...)
        },
        function(){
        	$(this).css(..)
        }
        );
        return $(this)
  	}
  });
  
})(jquery)

```