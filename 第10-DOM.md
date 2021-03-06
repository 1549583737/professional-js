## DOM

> DOM（文档对象模型），是针对HTML和XML文档的一个API，DOM描述了一个层次化的节点树，允许开发人员`添加`，`移除`,`修改`页面的某一部分。

## 目标

1. 理解包含不同层次节点的DOM
2. 使用不同的节点类型(一般是元素节点，文本节点，文档碎片，文档节点等)
3. 克服浏览器的兼容性问题及各种陷阱

## 节点的类型

> 接下来会简要的总结常见的几种节点类型以及其相关的知识点

## Node类型

> DOM1定义了一个Node借口，所有的元素都有`nodeType`属性，nodeType可取得值有12中，常见和经常用的有以下几种

1. 1 (元素节点)
2. 3 (文本节点)
3. 9 (文档节点)
4. 11 (文档碎片`DocumentFragment`)

## childNodes

> 每个节点都有`childNodes`属性，其保存着一种类数组对象，用于保存一组有序的节点，可以用下标方式去访问，也可以用`item`方法去访问,当然也要注意，childNodes属性有浏览器的兼容问题，ie下只包含其子节点中为元素节点的子元素，其他浏览器则还包括元素节点


``` javascript
var eles = someNode.childNodes
var len = eles.length
var firstChild = ele[0] or eles.item(0)
var lastChild = eles[len - 1] or eles.item(len - 1)

```

## 节点之间的关系

> 节点之间的关系是多样的，两个节点之间可以父子节点，祖孙节点，兄弟节点等等

**previousSibling**
**nextSibling**
**firstChild**
**lastChild**

当一个列表中只存在一个节点，那么previousSibling和nextSibling都为null

firstChild和lastChild也分别指向第一个和最后一个子节点


## 操作节点

> 我们可以用`appendChild`、`insertBefore`、`replaceChild`来进行常见的节点之间的操作

**parentNode.appendChild(childNode)**

1. 将childNode节点添加到parentNode节点末尾
2. 如果childNode节点已经在文档中存在，则从原来的位置移动到parentNode的末尾。

[appendChild用法链接](https://qianlongo.github.io/professional-js/examples/%E7%AC%AC%E5%8D%81%E7%AB%A0-DOM/%E6%93%8D%E4%BD%9C%E8%8A%82%E7%82%B9.html)

**parentNode.insertBefore(要插入的节点, 作为参照的节点)**

1. 如果`作为参照的节点`不为null，`则要插入的节点`最终会插入到`作为参照的节点`前面。
2. 如果`作为参照的节点`为null，则其作用与`appendChild`类似
3. 该方法执行之后返回`要插入的节点`

[insertBefore的用法](https://qianlongo.github.io/professional-js/examples/%E7%AC%AC%E5%8D%81%E7%AB%A0-DOM/%E6%93%8D%E4%BD%9C%E8%8A%82%E7%82%B9.html)

**parentNode.replaceChild(要插入的节点, 要替换的节点)**

1. `要插入的节点`如果是原来已经存在，则从原来的位置移动到`要替换的节点`位置前面

[replaceChild的用法](https://qianlongo.github.io/professional-js/examples/%E7%AC%AC%E5%8D%81%E7%AB%A0-DOM/%E6%93%8D%E4%BD%9C%E8%8A%82%E7%82%B9.html)

**parentNode.removeChild(childNode)**

[removeChild的用法](https://qianlongo.github.io/professional-js/examples/%E7%AC%AC%E5%8D%81%E7%AB%A0-DOM/%E6%93%8D%E4%BD%9C%E8%8A%82%E7%82%B9.html)

**ele.cloneNode(true or other)**

1. 克隆节点，如果传入的值为true，则深度克隆，包括文本节点等
2. 如果传入为false 或者不传入，则浅复制该节点本身
3. 注意复制节点并不会连同事件也复制，但是ie有bug，会连同事件一起复制

[cloneNode的用法](https://qianlongo.github.io/professional-js/examples/%E7%AC%AC%E5%8D%81%E7%AB%A0-DOM/%E6%93%8D%E4%BD%9C%E8%8A%82%E7%82%B9.html)








