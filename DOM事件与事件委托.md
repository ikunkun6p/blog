# 什么是DOM事件？

DOM (文档对象模型)结构是一个树型结构，当一个 HTML 元素产生一个事件时，该事件会在元素节点与根结点之间的路径传播，路径所经过的结点都会收到该事件，这个传播过程可称为 DOM 事件流。

### 传播按顺序分为三个阶段：捕获阶段、目标阶段、冒泡阶段

## 点击事件：

W3C2002年发布了W3C标准。文档名为DOM Level 2 Events Specification。
规定了浏览器应该同时支持两种调用顺序，
爷爷→爸爸→儿子顺序看有没有函数监听。儿子→爸爸→爷爷看有没有函数监听。
有监听就调用函数并提供事件信息，没有的话就跳过。
术语：
从外向内找叫事件捕获。从内向外叫事件冒泡。
开发者自己选择是把fnYe 放在捕获或者冒泡阶段。


### addEventListener：
事件绑定API：
IE： baba.attachEvent('onclick', fn)  // 冒泡
网景：baba.addEventListener('click', fn)  // 捕获
W3C：baba.addEventListener('click', fn, bool) // 第三个参数决定是冒泡还是捕获
如果bool不传或为falsy值，就让fn冒泡。bool为true就让fn走捕获。

答疑：
如果点击了儿子，就算点击了老子。但先调用谁不确定。
## 捕获与冒泡：
捕获阶段会先调用爸爸的监听事件函数，冒泡会先调用儿子的监听事件函数。
W3C事件模型：
先捕获（先爸爸→儿子），再冒泡？（儿子→爸爸）。
e对象会被传给所有监听函数，事件结束后，e对象就消亡。

### taeget vs currentTarget
区别：
e.target  用户操作的元素
e.currentTarget  程序员监听的元素
this 是 e.currentTarget， 不太推荐使用。
例： 
div > span {文字}，用户点击文字
e.target 就是 span，e.currentTarget就是div
特例：
当只有一个div被监听时，且不用考虑父子级关系，用户操作的元素就是被监听的元素。
按代码顺序执行。
代码：
```
div.addEventListener('click', f1)
div.addEventListener('click', f2, true)  //  f1 先执行，因为f1先被监听
```

### 取消冒泡：
捕获阶段无法被取消，但冒泡阶段可以。
e.stopPropagation() 可以中断冒泡。一般用于封装某些独立组件。
但某些事件不可以取消冒泡：scroll event。

### 如何阻止滚动事件：
```
x.addEventListener('wheel', (e) => {  // 取消掉浏览器右侧滚动条
  e.preventDefault()
})
x.addEventListener('touchstart'), (e) => {   // 阻止手机触屏滚动
  e.preventDefault()
})
```
自定义事件：浏览器自带的事件
```
<div id=div1>
<button id=button1> 点击触发frank事件</button>
</div>

button1.addEventListener('click', () => {
  const event = new CustomEvent('frank' , { 
    detail: {name:'frank', age: 18},
    bubblues: true,
    cancelable: false
})
  button1.dispatchEvent(event)
})
div.addEventListener('frank', (e) => {
  console.log('frank 事件被触发了)
  console.log(e.detail)
})
```
事件委托：
应用场景：
1、要监听100个按钮，添加点击事件，怎么做？
答：直接监听这100个按钮的祖先，等冒泡阶段判断target是不是这100个按钮中的其中一个。
2、你要监听目前不存在的元素的点击事件，怎么做？
答：监听祖先，等点击的时候看看是不是你想要的监听元素即可。
这样做的优点是可以节约内存，并且可以监听动态元素。

封装事件委托：
```
on('click', '#div1', 'button', () => {
  console.log('button 被点击了')
})
function on(eventType, element, selector, fn) {
  if (!(element instanceof Element)) {
    element = document.querySelecotor(element)
  }
  element.addEventListener(eventType, (e) => {
    const t = e.target
    if (t.matches(selector)) {
      fn(e)
    }
  }) // 这是一个错误代码，但是在面试时可以使用这个思路逻辑
}
```
答案：给元素添加一个监听事件，看当前的target是不是满足selector，如果满足就调用函数，如果不满足就放过。
正确代码：
```
function on(eventType, element, selector, fn) {
  if (!(element instanceof Element)) {
    element = document.querySelector(element)
  }
  element.addEventListener(eventType, e => {
    let el = e.target
    while (!el.matches(selector)) {
      el = null
      break
      }
      el = el.parentNode
    }
    el && fn.call(el, e, el)
  })
  return element
}
```

JS是否支持事件？
答：支持，也不支持。DOM事件不属于JS的功能，术语浏览器提供的DOM功能。JS只是调用了DOM提供的addEventListener。
