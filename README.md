# Interview-Points
这是从各个论坛博客的文章中得来的，自己稍加改造一下整理的一些面试知识点:computer:

# 目录
<!-- TOC -->

- [Interview-Points](#interview-points)
- [目录](#目录)
- [1. 模拟new的过程](#1-模拟new的过程)
- [2. 函数防抖和节流](#2-函数防抖和节流)
- [3. 输入url到展示的过程](#3-输入url到展示的过程)
- [4. 函数的柯里化](#4-函数的柯里化)
- [5. 重绘与回流](#5-重绘与回流)
  - [1. 重绘](#1-重绘)
  - [2. 回流](#2-回流)
  - [如何避免重绘和回流](#如何避免重绘和回流)
- [6. 浏览器存储](#6-浏览器存储)
- [7. 网络请求方式](#7-网络请求方式)
- [8. TCP三次握手](#8-tcp三次握手)
- [9. TCP四次挥手](#9-tcp四次挥手)
- [10. 内存泄漏](#10-内存泄漏)
- [11. 类继承的特点](#11-类继承的特点)
- [12. 常用正则表达式](#12-常用正则表达式)
- [13. 跨域](#13-跨域)
  - [跨域行为](#跨域行为)
  - [JSONP](#jsonp)
  - [CORS跨域](#cors跨域)
  - [简单请求](#简单请求)
  - [非简单请求](#非简单请求)
  - [CORS 与 JSONP的对比](#cors-与-jsonp的对比)
- [14. 缓存](#14-缓存)
  - [强缓存](#强缓存)
  - [协商缓存](#协商缓存)
  - [缓存场景](#缓存场景)
- [15. 手写call、apply、bind](#15-手写callapplybind)
- [16. 伪类和伪元素的区别](#16-伪类和伪元素的区别)
  - [伪类](#伪类)
  - [伪元素](#伪元素)
  - [区别](#区别)
- [17. 绝对定位](#17-绝对定位)
- [18. window.onload,doument.onload的区别](#18-windowonloaddoumentonload的区别)
- [19. 事件委托](#19-事件委托)
  - [事件冒泡](#事件冒泡)
  - [事件委托的优点](#事件委托的优点)
  - [注意](#注意)
- [20. instanceof的的实现原理](#20-instanceof的的实现原理)
- [21. 继承](#21-继承)
- [22. for...in 和 for...of](#22-forin-和-forof)
- [23. 数组扁平化](#23-数组扁平化)
- [24. 前端性能优化](#24-前端性能优化)
- [25. js实现动画](#25-js实现动画)
- [26. 实现autocomplete属性](#26-实现autocomplete属性)
- [27. 代码实现深拷贝](#27-代码实现深拷贝)
- [28. 乱序算法](#28-乱序算法)
- [29. 数组去重](#29-数组去重)
- [30. React中的key作用](#30-react中的key作用)
  - [概述](#概述)
  - [反模式](#反模式)
  - [总结](#总结)
- [31. React系列](#31-react系列)
  - [组件的render函数在何时被调用](#组件的render函数在何时被调用)
  - [组件的生命周期](#组件的生命周期)
  - [Virtual Dom](#virtual-dom)
  - [setState同步？异步？](#setstate同步异步)
- [32. React常见面试题](#32-react常见面试题)
  - [调用setState之后发生了什么](#调用setstate之后发生了什么)
  - [React中Element和Component的区别](#react中element和component的区别)
  - [什么情况下你会优先选择使用Class Component而不是Functional Component](#什么情况下你会优先选择使用class-component而不是functional-component)
  - [React中refs的作用是什么](#react中refs的作用是什么)
  - [React中keys的作用](#react中keys的作用)
  - [受控组件与非受控组件的区别](#受控组件与非受控组件的区别)
  - [在声明周期中哪一步应该发起Ajax请求](#在声明周期中哪一步应该发起ajax请求)
  - [shouldComponentUpdate的作用是什么，为何他如此重要](#shouldcomponentupdate的作用是什么为何他如此重要)
  - [React中的事件处理逻辑](#react中的事件处理逻辑)
  - [createElement和cloneElement的区别是什么](#createelement和cloneelement的区别是什么)
  - [setState函数的第二个参数的作用是什么](#setstate函数的第二个参数的作用是什么)
  - [为什么虚拟dom会提高性能](#为什么虚拟dom会提高性能)
  - [diff算法](#diff算法)
  - [diff算法的三种优化策略](#diff算法的三种优化策略)
  - [react性能优化](#react性能优化)
  - [简述Flux思想](#简述flux思想)
  - [展示组件（Presentational component）和容器组件（Container component）之间有何不同](#展示组件presentational-component和容器组件container-component之间有何不同)
  - [组件的状态（state）和属性（props）有何区别](#组件的状态state和属性props有何区别)
  - [什么是高阶组件](#什么是高阶组件)
  - [为什么建议setState的参数是一个callback而不是对象](#为什么建议setstate的参数是一个callback而不是对象)
  - [除了在构造函数绑定this，还有其他办法吗](#除了在构造函数绑定this还有其他办法吗)
  - [构造函数中为什么要调用super](#构造函数中为什么要调用super)
  - [React的三种构建组件的方式](#react的三种构建组件的方式)
  - [useEffect和useLayoutEffect的区别](#useeffect和uselayouteffect的区别)
  - [实现 useState 和 useEffect](#实现-usestate-和-useeffect)
  - [React新特性](#react新特性)
  - [React 状态提升](#react-状态提升)
  - [高阶函数](#高阶函数)
    - [属性代理](#属性代理)
    - [反向继承](#反向继承)
  - [HOC存在的问题](#hoc存在的问题)
  - [HOC约定](#hoc约定)
  - [应用场景](#应用场景)
- [33. CSRF 和 XSS](#33-csrf-和-xss)
  - [区别](#区别-1)
  - [CSRF](#csrf)
  - [XSS](#xss)
  - [总结](#总结-1)
- [34. localStorage 和 sessionStorage 和 cookie](#34-localstorage-和-sessionstorage-和-cookie)
  - [localStorage](#localstorage)
  - [sessionStorage](#sessionstorage)
  - [cookie](#cookie)
  - [总结](#总结-2)
- [35. BFC 及其作用](#35-bfc-及其作用)
- [36. 实现 (5).add(3).minus(2) 功能](#36-实现-5add3minus2-功能)
- [37. 连续赋值](#37-连续赋值)
- [38. display: none, visibility: hidden 和 opacity: 0](#38-display-none-visibility-hidden-和-opacity-0)
- [39. for 和 forEach 的性能](#39-for-和-foreach-的性能)
- [40. react-router的`<Link>` 和 `<a>` 有何区别](#40-react-router的link-和-a-有何区别)
- [41. 执行上下文](#41-执行上下文)
- [42. 执行栈](#42-执行栈)
- [43. 创建执行上下文](#43-创建执行上下文)
  - [创建阶段](#创建阶段)
    - [this绑定](#this绑定)
    - [词法环境](#词法环境)
    - [变量环境](#变量环境)
- [44. 事件循环](#44-事件循环)
- [45. link 与 @import](#45-link-与-import)
- [46. 外边距重叠](#46-外边距重叠)
- [47. 渐进增强 和 优雅改进](#47-渐进增强-和-优雅改进)
- [48. 立即执行函数](#48-立即执行函数)
- [49. HTTP2.0 与 HTTP1.1](#49-http20-与-http11)
  - [HTTP2.0](#http20)
  - [HTTP1.1](#http11)
- [50. css动画与js动画的区别](#50-css动画与js动画的区别)
- [51. offset、client和scroll的属性](#51-offsetclient和scroll的属性)
- [52. 手撕代码题](#52-手撕代码题)
- [53. 行内元素的margin 和 padding](#53-行内元素的margin-和-padding)
- [54. 行内元素和块级元素](#54-行内元素和块级元素)
- [55. margin、padding和translate百分比是按照什么计算的](#55-marginpadding和translate百分比是按照什么计算的)
- [56. display: inline-block元素之间有间隙](#56-display-inline-block元素之间有间隙)
- [57. HTTPS原理](#57-https原理)
  - [加密过程](#加密过程)
  - [对称加密和非对称加密](#对称加密和非对称加密)
  - [数字证书和数字签名](#数字证书和数字签名)
  - [握手过程](#握手过程)
  - [使用](#使用)
- [58. setImmediate() 和 process.nextTick()](#58-setimmediate-和-processnexttick)
- [59. 浏览器和node的事件循环](#59-浏览器和node的事件循环)
  - [Node环境下](#node环境下)
  - [区别](#区别-2)
  - [总结](#总结-3)
- [60. React Fiber](#60-react-fiber)
  - [Scheduler](#scheduler)
  - [Fiber数据结构](#fiber数据结构)
  - [任务拆分](#任务拆分)
  - [任务暂停](#任务暂停)
  - [优先级](#优先级)
- [61. webpack流程](#61-webpack流程)
- [62. webpack的热更新](#62-webpack的热更新)
- [63. CommonJs 与 ES6模块化区别](#63-commonjs-与-es6模块化区别)
- [64. 箭头函数和普通函数](#64-箭头函数和普通函数)
- [65. node读取文件转换为buffer](#65-node读取文件转换为buffer)
- [66. sort函数](#66-sort函数)
- [67. 闭包 和 自执行函数](#67-闭包-和-自执行函数)
  - [闭包](#闭包)
  - [自执行函数](#自执行函数)
  - [区别](#区别-3)
- [68. 0.1 + 0.2 ！== 0.3](#68-01--02--03)
- [69. React服务端渲染](#69-react服务端渲染)
  - [优点](#优点)
  - [弊端](#弊端)
- [70. 前端路由的原理](#70-前端路由的原理)
- [71. Mobx原理](#71-mobx原理)
  - [工作原理](#工作原理)
  - [设计原则](#设计原则)
- [72. Object.create()实现原理](#72-objectcreate实现原理)
- [73. 事件穿透](#73-事件穿透)
- [74. 常见http状态码](#74-常见http状态码)
- [75. js、css阻塞](#75-jscss阻塞)
  - [内嵌和外部js](#内嵌和外部js)
  - [css](#css)
- [76. 隐式转换](#76-隐式转换)
- [77. React首屏优化](#77-react首屏优化)
- [78. Object.assign](#78-objectassign)
- [79. innerHtml 和 outerHtml](#79-innerhtml-和-outerhtml)
- [80. rem 和 em](#80-rem-和-em)
- [81. 垃圾回收机制 和 内存泄漏](#81-垃圾回收机制-和-内存泄漏)
  - [垃圾回收](#垃圾回收)
  - [内存泄漏](#内存泄漏)
  - [优化](#优化)
- [82. 手写Promise 和 Promise.all](#82-手写promise-和-promiseall)
  - [Promise](#promise)
  - [Promise.all](#promiseall)
- [83. post的方法](#83-post的方法)
- [84. http options预检请求](#84-http-options预检请求)
- [85. oop三大特点](#85-oop三大特点)
- [86. 手写限制并发数](#86-手写限制并发数)
- [87. webpack的tree shaking](#87-webpack的tree-shaking)
- [88. getComputedStyle 和 style](#88-getcomputedstyle-和-style)
- [89. 怪异盒模型](#89-怪异盒模型)
- [90. Object.defineProperty](#90-objectdefineproperty)
- [91. HTTP如何复用连接](#91-http如何复用连接)
- [92. HTTP和TCP的关系](#92-http和tcp的关系)
- [93. node的优势](#93-node的优势)
- [94. HTTP报文结构](#94-http报文结构)
  - [请求头](#请求头)
  - [响应头](#响应头)
- [95. async / await](#95-async--await)
  - [async](#async)
  - [await](#await)
  - [与generator的区别](#与generator的区别)
- [96. 是否每一次请求都会三次握手](#96-是否每一次请求都会三次握手)
- [97. TCP的keepAlive和HTTP的keep-alive](#97-tcp的keepalive和http的keep-alive)
- [98. TCP两次握手可不可以呢](#98-tcp两次握手可不可以呢)
- [99. TCP三次握手中可以传输数据吗](#99-tcp三次握手中可以传输数据吗)
- [100. 2MSL等待状态](#100-2msl等待状态)
- [101. websocket](#101-websocket)
- [102. hasOwnProperty](#102-hasownproperty)

<!-- /TOC -->

# 1. 模拟new的过程
实现步骤
1. 创建一个新的对象obj
2. 链接到原型（新对象的原型指向要继承的构造函数的原型），obj可以访问构造函数原型的属性
3. 绑定this实现继承，obj可以访问构造函数的属性
4. 如果构造函数返回的是对象则返回它，如果不是则返回obj
```javascript
function Animals(name, color){
    this.name = name
} 

Animals.prototype.action = function () {
  console.log(this.name, 'walk')
```
首先定义一个构造函数，以及他原型的方法  
接着实现一个`create`方法来模拟new
```javascript
function create(constructor, ...args){
    const obj = new Object()
    obj.__proto__ = constructor.prototype
    const res = constructor.apply(obj, args)
    return res instanceof Object ? res : obj
}
```
具体使用则：
```javascript
const dog = create(Animals, 'dog', 'red')

// const cat = new Animals('cat', 'yellow')
```
> 通过改变一个对象的 [[Prototype]] 属性来改变和继承属性会对性能造成非常严重的影响，并且性能消耗的时间也不是简单的花费在 obj.__proto__ = ... 语句上, 它还会影响到所有继承自该 [[Prototype]] 的对象，如果你关心性能，你就不应该修改一个对象的 [[Prototype]]。  

所以我们可以通过别的方法来改变obj原型的指向，通过`Object.create()`方法来继承
```javascript
function create(constructor, ...args) {
  const obj = Object.create(constructor.prototype)
  const res = constructor.apply(obj, args)
  return res instanceof Object ? res : obj
}
```

# 2. 函数防抖和节流
首先模拟一下用户输入
```html
<div>
  <input id="input"></input>
  <div id="text">0</div>
</div>
```

然后防抖与节流
```javascript
// 防抖
const debounce = function (fn, delay = 1000) {
  let time = null
  return function (...args) {
    let that = this
    time && clearTimeout(time)
    time = setTimeout(function () {
      fn.apply(that, args)
    }, delay)
  }
}

// 节流
const throttle = function (fn, delay = 1000) {
  let time = null
  return function (...args) {
    let that = this
    if (!time) {
      time = setTimeout(function () {
        time = null
        fn.apply(that, args)
      }, delay)
    }
  }
}
```

接下来调用即可
```javascript
const input = document.getElementById('input')
input.oninput = debounce((e) => {
  document.getElementById('text').innerTexte.target.value
}, 1500)
```
这样子就可以实现函数防抖和节流啦  

其实这里还有另外一个简单一点的方法，就是setTimeout使用箭头函数，这样就可以直接使用`this`，就不用额外生成一个变量`that`啦
```javascript
const debounce = function (fn, delay = 1000) {
  let time = null
  return function (...args) {
    time && clearTimeout(time)
    time = setTimeout(() => {
      fn.apply(this, args)
    }, delay)
  }
}
```

# 3. 输入url到展示的过程
1. DNS解析
2. TCP三次握手
3. 发送请求，分析url，设置请求头
4. 服务器返回请求的文件（html）
5. 浏览器渲染
    - 解析html文件，生成dom树
    - 解析css文件，生成style树
    - 结合dom树和style树，生成渲染树（render tree）
    - layout布局渲染
    - GPU像素绘制页面


# 4. 函数的柯里化
```
// 实现一个add方法，使计算结果能够满足如下预期：
add(1)(2)(3) = 6;
add(1, 2, 3)(4) = 10;
add(1)(2)(3)(4)(5) = 15;
```
主要是要收集传进来的参数
```javascript
function curry(){
    const argsList = [...arguments]
    
    const fn = function(){
        argsList.push(...arguments)
        return fn
    }
    
    fn.toString = function(){
        return argsList.reduce((a, b) => a + b)
    }
    
    return fn
}

console.log(curry(1, 2)(3)(4, 5, 6)) // 21
```
这样就算完成了这个题了，可以自由传入参数来求和，接下来就将一个普通函数变成柯里化函数
```javascript
function sum(a, b, c) {
  return a + b + c
}
function curry(fn) {
  const argsList = [...arguments].splice(1)
  return function () {
    const newArgsList = argsList.concat([...arguments])
    if (newArgsList.length < fn.length) {
      // 如果接收的参数还没有到达函数参数的个数继续收集参数
      return curry.apply(this, [fn, ...newArgsList])
    } else {
      return fn.apply(this, newArgsList)
    }
  }
}
const sumAll = curry(sum)
console.log(sumAll(1)(2)(3)) // 6
console.log(sumAll(1)(2, 3)) // 6
```

# 5. 重绘与回流
## 1. 重绘
当元素样式发生改变，但不影响布局时，浏览器将使用重绘进行元素更新，由于此时只需要UI层面的绘制，因此损耗较小

## 2. 回流
当元素尺寸、结构或者触发某些属性的时候，浏览器会重新渲染页面，这就叫回流。此时，浏览器需要重新计算，重新进行页面布局，所以损耗较大  

一般有以下几种操作：
- 页面初次渲染
- 浏览器窗口大小改变
- 元素尺寸、位置、内容改变
- 元素字体大小改变
- 添加或删除可见的dom元素
- 触发CSS伪类，如`:hover`
- 查询某些属性或者调用某些方法
    - clientWidth, clientHeight, clientTop, clientLeft
    - offsetWidth, offsetHeight, offsetTop, offsetLeft
    - scrollWidth, scrollHeight, scrollTop, scrollLeft
    - getComputedStyle()
    - getBoundingClientRect()
    - scrollTo()

**回流必定触发重绘，重绘不一定触发回流，重绘代价小，回流代价大**

## 如何避免重绘和回流
CSS: 
- 避免使用table布局
- 尽可能再dom树的末端修改class
- 避免使用多层内联样式
- 将动画效果应用到`position: absolute || fixed`上
- 避免使用css表达式（例如`calc`）
- CSS3硬件加速（GPU加速）

JavaScript:
- 避免频繁操作样式，最好一次性修改style属性，或者将样式列表定义成class，并一次性更改class属性
- 避免频繁操作dom，创建一个`documentFragment`，在他上面应用所有的dom操作，最后再把他添加到文档中
- 也可以先为元素设置`display: none`，操作结束后再把它显示出来，因为再display为none的元素上进行dom操作不会引发重绘和回流
- 避免频繁读取会引发重绘回流的属性，如果需要多次使用，就用一个变量缓存起来
- 对具有复杂动画的元素使用绝对定位，使他脱离文档流，否则会引起父元素及后续元素频繁回流

# 6. 浏览器存储
- `cookie` 通常用于存用户信息，登录状态等，可自行设置过期时间，体积上限为4K
- `localStorage` 无限期存储，体积上限为4~5M
- `sessionStorage` 浏览器窗口关闭则删除，体积上线为4~5M

# 7. 网络请求方式
- `get` 会被浏览器缓存，请求长度受限，会被历史保存记录
- `post` 更安全，更多编码类型，可以发大数据

# 8. TCP三次握手
为什么要TCP握手呢
> 为了防止已失效的连接请求报文段突然又传回服务端，从而产生错误

1. 客户端发送syn（同步序列编号）请求，进入syn_send状态，等待确认
2. 服务端接受syn包并确认，发送syn + ack包，进入syn_recv状态
3. 客户端接受syn + ack包，发送ack包，双方进入established状态

# 9. TCP四次挥手
1. 客户端发送fin给服务端，用于关闭client到server的数据传输。客户端进入fin_wait状态
2. 服务端接受fin后，发送一个ack包给客户端。服务端进入close_wait状态
3. 服务端发送一个fin给客户端，用于关闭server到client的数据传输。服务端进入last_ack状态
4. 客户端收到fin后，进入time_wait状态，接着发送一个ack给服务端，服务端进入closed状态

> 为什么建立是3次握手，而关闭是4次挥手呢？  

因为建立连接的时候，客户端接受的是syn + ack包。而关闭的时候，服务端接受fin后，客户端仅仅是不再发送数据，但是还是可以接收数据的。服务端此时可以选择立刻关闭连接，或者再发送一些数据之后，再发送fin包来关闭连接。因此fin与ack包一般都会分开发送。


# 10. 内存泄漏
- 意外的全局变量
- 闭包
- 未被清空的定时器
- 未被销毁的事件监听
- dom引用

# 11. 类继承的特点
```javascript
class Dog {
  constructor(name) {
    this.name = name;
  }
}

class Labrador extends Dog {
  // 1 
  constructor(name, size) {
    this.size = size;
  }
  
  // 2 
  constructor(name, size) {
    this.name = name;
    this.size = size;
  }
  
  // 3
  constructor(name, size) {
    super(name);
    this.size = size;
  }
};
```
像上面的代码，1和2都会报错`ReferenceError`引发一个引用错误，因为在子类中，在调用`super`之前，是无法访问`this`的

# 12. 常用正则表达式
```
验证数字的正则表达式集

验证数字：^[0-9]*$

验证n位的数字：^\d{n}$

验证至少n位数字：^\d{n,}$

验证m-n位的数字：^\d{m,n}$

验证零和非零开头的数字：^(0|[1-9][0-9]*)$

验证有两位小数的正实数：^[0-9]+(.[0-9]{2})?$

验证有1-3位小数的正实数：^[0-9]+(.[0-9]{1,3})?$

验证非零的正整数：^\+?[1-9][0-9]*$

验证非零的负整数：^\-[1-9][0-9]*$

验证非负整数（正整数 + 0） ^\d+$

验证非正整数（负整数 + 0） ^((-\d+)|(0+))$

验证长度为3的字符：^.{3}$

验证由26个英文字母组成的字符串：^[A-Za-z]+$

验证由26个大写英文字母组成的字符串：^[A-Z]+$

验证由26个小写英文字母组成的字符串：^[a-z]+$

验证由数字和26个英文字母组成的字符串：^[A-Za-z0-9]+$

验证由数字、26个英文字母或者下划线组成的字符串：^\w+$

验证用户密码:^[a-zA-Z]\w{5,17}$ 正确格式为：以字母开头，长度在6-18之间，只能包含字符、数字和下划线。

验证是否含有 ^%&',;=?$\" 等字符：[^%&',;=?$\x22]+

验证汉字：^[\u4e00-\u9fa5],{0,}$

验证Email地址：^\w+[-+.]\w+)*@\w+([-.]\w+)*\.\w+([-.]\w+)*$

验证InternetURL：^http://([\w-]+\.)+[\w-]+(/[\w-./?%&=]*)?$ ；^[a-zA-z]+://(w+(-w+)*)(.(w+(-w+)*))*(?S*)?$

验证电话号码：^(\d3,4\d3,4|\d{3,4}-)?\d{7,8}$：--正确格式为：XXXX-XXXXXXX，XXXX-XXXXXXXX，XXX-XXXXXXX，XXX-XXXXXXXX，XXXXXXX，XXXXXXXX。

验证身份证号（15位或18位数字）：^\d{15}|\d{}18$

验证一年的12个月：^(0?[1-9]|1[0-2])$ 正确格式为：“01”-“09”和“1”“12”

验证一个月的31天：^((0?[1-9])|((1|2)[0-9])|30|31)$ 正确格式为：01、09和1、31。

整数：^-?\d+$

非负浮点数（正浮点数 + 0）：^\d+(\.\d+)?$

正浮点数 ^(([0-9]+\.[0-9]*[1-9][0-9]*)|([0-9]*[1-9][0-9]*\.[0-9]+)|([0-9]*[1-9][0-9]*))$

非正浮点数（负浮点数 + 0） ^((-\d+(\.\d+)?)|(0+(\.0+)?))$

负浮点数 ^(-(([0-9]+\.[0-9]*[1-9][0-9]*)|([0-9]*[1-9][0-9]*\.[0-9]+)|([0-9]*[1-9][0-9]*)))$

浮点数 ^(-?\d+)(\.\d+)?$

```

# 13. 跨域
## 跨域行为
- 同源策略限制、安全性考虑（如cookies）
- 协议、IP地址和端口不同都是跨域行为

## JSONP
```javascript
const script = document.createElement('script')
script.type = 'text/javascript'

script.src = 'xxx.com/login?user=xxx&password=123&callback=onBack'
document.head.appendChild(script)

function onBack(res) {
    console.log(res)
}
```

## CORS跨域
> CORS (Cross-Orgin Resources Share)跨域资源共享，允许浏览器向服务器发出XMLHttpRequest请求，从而克服跨域问题，他需要浏览器与服务器同时支持  

- 浏览器端会自动向请求头添加`orgin`字段，表明当前请求来源
- 服务器需要设置响应头的`Access-Control-Allow-Methods`，`Access-Control-Allow-Headers`，`Access-Control-Allow-Origin`等字段，指定允许的方法、头部、来源等信息
- 请求分为简单请求和非简单请求，非简单请求会先进行一次`OPTIONS`请求来判断当前是否允许跨域

## 简单请求
请求方法是以下三种之一：
- HEAD
- POST
- GET

Http的请求头信息不超过以下几种字段：
- Accept
- Accept-Language
- Content-Language
- Last-Event-ID
- Content-Type （只限三个值：`application/x-www-form-urlencoded`、`multipart/form-data`、`text/plain`）

后端的响应头信息：
- `Access-Control-Allow-Orgin`：此字段必须有，他的值要么是请求时`orgin`的值，要么是*表示接受任意域名的访问
- `Access-Control-Allow-Credentials`：此字段可选，是一个布尔值，用来表示是否允许发送`cookies`
- `Access-Control-Expose-Headers`：此字段可选，如果想XMLHttpRequest对象的`getResponseHeader()`方法获取更多请求头，就要在这个字段指定

## 非简单请求
非简单请求是指对服务器有特殊要求的请求，例如：
- 请求方法为`PUT`和`DELETE`
- `Content-Type`为`application/json`

非简单请求会在正式通信之前，增加一次HTTP查询请求，称为预检请求，就是`options`啦

- `Access-Control-Request-Methor`：此字段必须有，用来表示浏览器的CORS请求会用到哪些HTTP方法，例如`PUT`
- `Access-Control-Request-Headers`：此字段是一个逗号分隔的字符串，指定浏览器CORS请求会额外发送的请求头信息

## CORS 与 JSONP的对比
- JSONP只可以用于`GET`请求，CORS支持所有类型的HTTP请求
- JSONP的优势是支持老式浏览器，以及可以向不支持CORS的网站发送请求

# 14. 缓存
> 其实平时开发使用`webpack`进行构建的时候，后缀有hash值，其实这就是与缓存相关的东西

缓存可以分为强缓存和协商缓存。强缓存不过服务器，协商缓存需要过服务器。协商缓存返回的状态码是304。两种缓存可以同时存在，强缓存的优先级大于协商缓存。当执行强缓存时，如若缓存命中，则直接使用缓存数据库中的数据，不执行协商缓存。

## 强缓存
**Expires (HTTP 1.0)**：`Expires`的值为服务端返回的数据过期时间。当再次请求时间小于过期时间，则直接使用缓存数据。但由于服务端和客户端的时间可能有误差，可能会出现缓存命中的误差。另外，大多数使用`Cache-Control`代替

**Pragma (HTTP 1.0)**：HTTP 1.0遗留下来的字段，当值为`no-cache`时强制验证缓存，Pragma禁用缓存，如果给`Expires`定义一个未过期的时间，那么Pragma的优先级更高。服务端响应添加`Pragma: no-cache`，浏览器表现的行为和刷新(F5)相似

**Cache-Control (HTTP 1.1)**：有以下几种属性
- private：客户端可以缓存
- public：客户端和代理服务器都可以缓存
- max-age=t：缓存内容将在t秒后失效
- no-cache：需要使用协商缓存来验证缓存数据
- no-store：所有内容都不会缓存

> no-cache不是代表不缓存的意思，no-cache代表的是可以缓存，但是每次都要通过服务器验证缓存是否可用。no-store才是不缓存内容。

当响应头`Cache-Control`有指定`max-age`时，优先级会比`expires`高。

命中强缓存的形式：Firefox浏览器：灰色的200状态码，Chrome浏览器：200(from disk cache)或者200 OK(from memory cache)

## 协商缓存
协商缓存需要进行对比判断是否可以使用缓存。浏览器第一次请求数据时候，服务器会将缓存标识与数据一起响应给客户端，客户端将他们备份至缓存中。再次请求时候，客户端会将缓存中的标识发送给服务端，服务端根据此表示判断。若未失效，返回304状态码，浏览器拿到此状态码，就可以直接使用缓存数据了。

**Last-Modified**：服务器再响应请求时，会告诉浏览器资源的最后修改时间

**if-Modified-Since**：浏览器再次请求服务器的时候，请求头会包含此字段，后面跟着在缓存中获得的最后修改时间。服务端收到此请求发现有`if-Modified-Since`后，则与被请求资源的最后修改时间进行对比，如果一致则返回304响应，浏览器只需要从缓存中获取数据即可
- 如果资源被修改了，服务端就传输一个整体数据，服务器返回200 OK
- 如果没有被修改，服务器只需要传输响应头信息，服务器返回 304 Not Modified

**if-Unmodified-Since**：从某个时间点开始，文件是否没有被修改，使用的是相对时间，不需要关心客户端与服务端的时间偏差。
- 如果没有被修改，则开始继续传送数据，服务器返回200 OK
- 如果文件被修改了，则不传输，服务器返回412 Precondition failed（预处理错误）

> 这两个的区别是一个修改了才下载，一个是没修改才下载。

如果在服务器上，一个资源被修改了，但是他的实际内容根本没有发生变化，会因为Last-Modified时间匹配不上而返回了整个数据给客户端（即使客户端缓存里面有一个一模一样的资源），为了解决这个问题，我们就需要用到HTTP 1.1的`Etag`

**Etag**：服务器响应请求时，通过此字段告诉浏览器当前资源在服务器生成的唯一标识（生成规则由服务器决定）

**If-Match**：条件请求，携带上一次请求中资源的`Etag`，服务器根据这个字段判断文件是否有新的修改

**If-None-Match**：再次请求服务器时，浏览器的请求报文头部会包含此字段，后面的值为在缓存中获取的标识，服务器接收到报文后发现`If-None-Match`则与被请求的资源的唯一表示进行对比
- 不同，说明资源被修改过，则相应整个资源内容，返回状态码200
- 相同，说明资源没有被修改，则响应header，浏览器直接从缓存中获取数据信息，服务器返回状态码304

**Etag 的精度比 Last-modified 高，属于强验证，要求资源字节级别的一致，优先级高。如果服务器端有提供 ETag 的话，必须先对 ETag 进行 Conditional Request。**

> 但是实际应用中由于`Etag`的计算是由算法得来的，而算法会占用服务器计算的资源，所有服务器端的资源都是宝贵的，所以就很少使用`Etag`了

- 浏览器输入URL地址，回车之后，浏览器发现缓存中已经有这个文件了，就不用继续请求，直接从缓存中获取数据信息
- F5刷新，就是浏览器向服务器发送一个请求，携带`If-Modified-Since`来查看文件是否过期
- Ctrl + F5强制刷新，就是先吧缓存中文件删除，然后再去服务器请求一个完整的资源，于是客户端就完成了强制更新的操作了

## 缓存场景
对于大部分的场景都可以使用强缓存配合协商缓存来解决，但是在一些特殊情况下，可能需要选择特殊的缓存策略
- 对于某些不需要缓存的资源，可以使用`Cache=Control: no-store`来表示该资源不需要缓存
- 对于频繁变动的资源，可以使用`Cache-Control: no-cache`并且配合`Etag`使用，表示该资源已被缓存，但是每次都会发送请求询问资源是否更新
- 对于代码文件来说，通常使用`Cache-Control: max-age=31536000`并且配合策略缓存使用，然后对文件进行指纹处理，一旦文件名变动就会立即下载新的文件

# 15. 手写call、apply、bind
```javascript
Function.prototype.myCall = function (obj = window) {
  obj.fn = this
  const args = [...arguments].splice(1)
  const result = obj.fn(...args)
  delete obj.fn
  return result
}

Function.prototype.myApply = function (obj = window) {
  obj.fn = this
  const args = arguments[1]
  let result = args ?
    obj.fn(...args) :
    obj.fn()
  delete obj.fn
  return result
}

Function.prototype.myBind = function (obj = window) {
  const that = this
  const args = [...arguments].splice(1)
  return function () {
    return that.apply(obj, [...args, ...arguments])
  }
}

// 然后使用即可
function log() {
  console.log(this)
  console.log(this.value)
  console.log(arguments)
}

const obj = {
  value: 123
}

log.myCall(obj, 1, 2, 3)
log.myApply(obj, [1, 2, 3])
log.myApply(obj)
log.myBind(obj)()
log.myBind(obj)(1, 2, 3)
log.myBind(obj, 4, 5, 6)(1, 2, 3)
```

# 16. 伪类和伪元素的区别
伪类和伪元素是为了修饰不在文档树中的部分，比如一句话的第一个字母，列表中第一个元素。

## 伪类
伪类用于当已有元素处于某种状态时候，为其添加对应的样式，这个状态是根据用户行为变化而变化的。比如说hover。虽然他和普通的css类似，可以为已有的元素添加样式，但是他只有处于dom树无法描述的状态才能为元素添加样式，**所以称为伪类**

## 伪元素
伪元素用于创建一些原本不在文档树中的元素，并为其添加样式，比如说`:before`。虽然用户可以看到这些内容，但是其实他不在文档树中。

## 区别
伪类的操作对象是文档树中已存在的元素，而伪元素是创建一个文档树外的元素。因此，伪类与伪元素的区别就在于：**有没有创建一个文档树之外的元素**

css规范中使用两个双冒号`::`来表示伪元素，一个冒号`:`来表示伪类。例如：`::before`，`:hover`


# 17. 绝对定位
- 父元素是块级元素，则子元素设置为父元素内边距的边界
- 父元素是行内元素，则子元素设置为父元素的内容边界

附上层叠上下文表
![image](https://user-gold-cdn.xitu.io/2019/8/30/16ce245b90085292?imageView2/0/w/1280/h/960/format/webp/ignore-error/1)

# 18. window.onload,doument.onload的区别
- window.onload：指页面上所有的dom，样式表，脚本，图片，flash都已经加载完成了的时候触发
- document.onload：指dom加载完成，不包括别的东西

# 19. 事件委托
> 事件委托就是把一个元素响应时间（click，keydown....）的函数委托到另一个元素。一般来说，会把一个或者一组元素的时间委托到父层或者更外层元素上。真正绑定事件的是外层元素，当事件响应到需要绑定的元素时候，会通过事件冒泡机制，从而触发他的外层元素的绑定事件上，然后再外层函数执行

## 事件冒泡
![image](https://lc-gold-cdn.xitu.io/a8d6c4231abb6134a7d1.png?imageView2/0/w/1280/h/960/format/webp/ignore-error/1)

事件模型分为三个阶段
- 捕获阶段：在事件冒泡的模型中，捕获阶段不会响应任何事件
- 目标阶段：目标阶段就是指事件响应到触发事件的最底层元素上
- 冒泡阶段：冒泡阶段就是事件的触发响应会从最底层目标一层一层向外到最外层元素（根节点），事件代理就是利用事件冒泡的机制，把内层需要响应的事件绑定到外层

## 事件委托的优点
1. 减少内存消耗
假设有一个列表，里面很多li，如果为他们每一个都绑定事件就很浪费内存，最好是把这个时间绑定到外层`ul`上统一处理
```
<ul id="list">
  <li>item 1</li>
  <li>item 2</li>
  <li>item 3</li>
  ......
  <li>item n</li>
</ul>
// ...... 代表中间还有未知数个 li
```
所以事件委托可以大量减少内存的消耗，节约效率

2. 动态绑定事件
假如我们需要做到动态增删列表内的元素，那么在每一次改变的时候又得重新进行事件绑定。如果用了事件委托就没有这烦恼了，因为事件绑定在父元素上，跟目标元素增删没有关系。

所以事件委托可以动态绑定时间，减少很多重复工作

```
window.onload = () => {
  const list = document.getElementById('list')
  list.addEventListener('click', function (event) {
    console.log(event.target)
  })
}

<ul class="list" id="list">
  <li>1</li>
  <li>2</li>
  <li>3</li>
</ul>
```

这样点击li标签的时间就会冒泡到ul上面，然后开始执行绑定的方法

## 注意
分情况分析:

- 有拿到节点的,优先捕获,没有才往上冒泡寻找
- 若是通过node.addEventListener('event',callback,bubble or capture); 谁先调用谁先执行

# 20. instanceof的的实现原理
```
while (x.__proto__) {
  if (x.__proto__ === y.prototype) {
    return true
  }
  x.__proto__ = x.__proto__.__proto__
}
if(x.__proto__ === null){
  return false
}
```
判断x对象是否为y的一个实例，会在原型链上一直找，找到则返回true

# 21. 继承
- 原型继承
```javascript
Student.prototype = new Person('b')
Student.prototype.constructor = Student
```
缺点：
1. 子类型无法超类型传递参数
2. 子类的方法必须写在`new Person`后面，不然会被覆盖

- 类式继承
```
function Child(name, parentName) {
    Parent.call(this, parentName);
    this.name = name;
}
```
缺点：
1. 没有原型，每次创建都会执行Parent.call

- 组合继承
```
function Child(name, parentName) {
    Parent.call(this, parentName);
    this.name = name;
}

Child.prototype = new Parent();      
Child.prototype.constructor = Child;
```
缺点：
1. 父类构造函数会被调用两次


- 寄生组合
```javascript
function Person(name) {
  this.name = name
}

Person.prototype.a = function () {
  console.log('person a')
}

Person.prototype.b = function () {
  console.log('person b')
}

function Student(name, superName) {
  Person.call(this, superName)
  this.name = name
}

Student.prototype = Object.create(Person.prototype)
Student.prototype.constructor = Student

Student.prototype.b = function () {
  console.log('student b')
}

const person = new Person('p')
const student = new Student('s')

console.log(person)
console.log(student)

person.a()
person.b()
student.a()
student.b()

console.log(student instanceof Person)
```

# 22. for...in 和 for...of
- for...in
for...in会遍历可遍历对象的所有属性
```
const arr = [5, 4, 3, 2, 1]
arr.name = 'name'

for(let i in arr){
  console.log(i) // 0 1 2 3 4 name(字符串类型的索引)
}
```
输出的是`0 1 2 3 4 name`，因为我们给arr加了一个name的属性，for...in也会把他遍历出来

所以for...in一般用于遍历对象，值是他的键值


- for...of
```
const arr = [5, 4, 3, 2, 1]
arr.name = 'name'

for(let i in arr){
  console.log(i) // 0 1 2 3 4 name(字符串类型的索引)
}
```
输出的是`5 4 3 2 1`，输入数组里面每个的值

**总结**
- for...of使用遍历数组/数组对象/字符串/map/set等拥有迭代器对象，但是不能遍历对象，因为对象没有迭代器对象。他可以使用break，continue，return
- for...in来遍历对象，或者使用`Object.keys()`
- for...in遍历的是数组的索引（键名），for...of是数组的值


# 23. 数组扁平化
```javascript
const test = [
  [1, 2, 2],
  [3, 4, 5, 5],
  [6, 7, 8, 9, [11, 12, [12, 13, [14]]]], 10
]

// 要求将以上数组扁平化排序且去重
// [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14]

// 递归版
function flat(arr) {
  let list = []
  arr.forEach(item => {
    if (Array.isArray(item)) {
      list.push(...flat(item))
      // list = list.concat(flat(item))
    } else {
      list.push(item)
    }
  })
  return list
}

const res1 = [...new Set(flat(test))].sort((a, b) => a - b)

// ES6版
const res2 = [...new Set(test.flat(Infinity))].sort((a, b) => a - b)

console.log(res1)
console.log(res2)
```

# 24. 前端性能优化
> https://csspod.com/frontend-performance-best-practices/

- 页面内容
    - 减少HTTP请求数
    - 减少DNS查询
    - 避免重定向
    - 缓存Ajax请求
    - 延迟加载
    - 预先加载
    - 减少dom元素数量
    - 划分不同内容到不同域名
    - 尽量减少使用iframe
    - 避免404错误
- 服务器
    - 使用CDN
    - 添加Expires或者Cache-Control响应头
    - 启用Gzip
    - 配置Etag
    - 尽早输出缓冲
    - Ajax请求使用get方法
    - 避免图片src为空
- Cookie
    - 减少cookie大小
    - 静态资源使用无cookie域名
- Css
    - 把样式表放在`<head>`中
    - 不要使用CSS表达式
    - 使用`<link`代替`@import`
    - 不要使用filter
- JavaScript
    - 把脚本放在页面底部
    - 使用外部JavaScript和Css
    - 压缩JavaScript和Css
    - 避免重复脚本
    - 减少dom操作
    - 使用高效的时间处理
- 图片
    - 优化图片
    - 优化CSS Sprite
    - 不要再HTML中缩放图片
    - 使用体积小、可缓存的favicon.ico
- 移动端
    - 保持单个文件小于25KB
    - 打包内容为分段（multipart）文档


# 25. js实现动画
> 将div平滑滑动，从快至慢，不能用css3的属性

```html
<!DOCTYPE html>
<html>

<head>
  <script>
    window.onload = () => {
      var element = document.getElementById('t');

      function step(timestamp) {
        console.log(timestamp)
        var progress = timestamp;
        // element.style.left = (progress / 30) * (10 - progress / 1000) + 'px';
        element.style.left = Math.pow(progress / 5, .5) * 40 + 'px';
        if (progress < 5000) {
          window.requestAnimationFrame(step);
        } else {
          window.cancelAnimationFrame(step)
        }
      }

      window.requestAnimationFrame(step);
    }
  </script>
  <style>
    .container {
      position: relative;
      width: 1000px;
    }

    #t {
      position: absolute;
      width: 50px;
      height: 50px;
      background: red;
    }
  </style>
</head>

<body>
  <div class="container">
    <div id="t"></div>
  </div>
</body>

</html>
```

# 26. 实现autocomplete属性
> 有一个input输入框，输入关键词的时候，模拟autocomplete效果补全

```html
<!DOCTYPE html>
<html>

<head>
  <script>
    window.onload = () => {

      const input = document.getElementById('input')
      const words = ['珠海', '广州', '上海', '杭州', '成都']
      input.addEventListener("input", debounce(function (e) {
        const value = e.target.value
        const index = words.findIndex((item) => value && item.indexOf(value) !== -1)
        if (index !== -1) {
          e.target.value = words[index]
        }
      }, 500))

      function debounce(fn, wait = 500) {
        let timeout = null
        return function () {
          if (timeout) {
            clearTimeout(timeout)
          }
          timeout = setTimeout(() => {
            fn.apply(this, [...arguments])
          }, wait)
        }
      }
    }
  </script>
  <style>
  </style>
</head>

<body>
  <input id="input" />
</body>

</html>
```

# 27. 代码实现深拷贝
```javascript
const deepClone = (obj) => {
  let result = null
  if (typeof obj === 'object') {
    result = Array.isArray(obj) ? [] : {}
    for (let key in obj) {
      if (obj.hasOwnProperty(key)) {
        if (obj[key] && typeof obj[key] === 'object') {
          result[key] = deepClone(obj[key])
        } else {
          result[key] = obj[key]
        }
      }
    }
  } else {
    // 如果不是对象与数组，则直接赋值
    result = obj
  }
  return result
}
```
或者使用自带方法
```javascript
JSON.parse(JSON.stringify(obj))
```


# 28. 乱序算法
`const arr = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]`

简单版
```javascript
arr.sort(() => Math.random() - 0.5)
```

洗牌算法
```javascript
const shuffle = (arr) => {
  let len = arr.length
  while (len > 1) {
    let index = Math.floor(Math.random() * len--);
    [arr[index], arr[len]] = [arr[len], arr[index]]
  }
  return arr
}
```

# 29. 数组去重
`const arr = [1, 1, 1, 2, 3, 4, 5, 5, 3, 2, 1, 1]`
简单版
```javascript
[...new Set(arr)]
```

循环版
```javascript
const removeDrop = function () {
  const result = []
  const map = {}
  arr.forEach((item) => {
    if (!map[item]) {
      map[item] = true
      result.push(item)
    }
  })
  return result
}
```

# 30. React中的key作用
## 概述
key是用来帮助react识别哪些内容被更改、添加或者删除。key值需要一个稳定值，因为如果key发生了变化，react则会触发UI的重渲染。
- 唯一性： key值必须唯一，如果出现了相同，会抛出警告，并且只会渲染第一个重复key值的元素。因为react会认为后续拥有相同key值的都是同一个组件。


- 不可读性： 虽然在组件定义了key，但是子组件中是无法获取key值的

## 反模式
现在有一个例子，我们不添加key的情况下，react会自动以索引的形式作为key值
```
let arr = ['first', 'second'];

// list1 和 list2 是等价的
const list1 = arr.map(item => <p>{item}</p>);
const list2 = arr.map((item, index) => <p key={index}>{item}</p>);
```

接着我们向数组末尾加一个元素，react经过diff算法之后，key值0和1的元素没有发生改变，所以UI上的操作只是仅仅在末尾添加多一个元素

但是如果在开头添加一个元素
```
<!-- before -->
<p key="0">first</p>
<p key="1">second</p>

<!-- after -->
<p key="0">zero</p>
<p key="1">first</p>
<p key="2">second</p>
```
所以元素的key值都发生了改变，这样每个元素都会重新渲染一次，性能就大大受到影响了

## 总结
简而言之，改变 key 值来重渲染组件是一种——相较于复杂componentWillReceiveProps生命周期——十分低成本的方式。

# 31. React系列
## 组件的render函数在何时被调用
每一次state的更改都会使得render函数被调用，但页面的dom不一定会发生修改

## 组件的生命周期
1. 初始化阶段（Mounting）
2. 更新阶段（Updating）
3. 析构阶段（Unmounting）


初始化阶段：
- constructor(): 用于绑定事件，初始化state
- componentWillMount(): 组件将要挂载，在render之前调用，每一个组件render之前就调用，一般在这操作state。可以在服务端调用
- render(): 用作渲染dom
- componentDidMount(): 在render之后，而且是所有子组件都render之后才调用，通常用于异步请求数据，因为在这里组件都初始化完成了

更新阶段：
- componentWillReceiveProps(nextProps): 在这里可以拿到即将改变的状态，可以在这里通过setState方法设置state
- shouldComponentUpdate(nextProps, nextState): 他的返回值决定了接下来的声明周期是否会被调用，默认返回true
- componentWillUpdate(): 不能在这里改变state，否则会陷入死循环
- componentDidUpdate(): 和componentDidMount()类似，在这里执行Dom操作以及发起网络请求

析构阶段
- componentWillUnmount(): 主要执行清除工作，比如取消网络请求，清除事件监听

## Virtual Dom
难点在于如何判断旧的对象和新的对象之间的差异
react的办法是只对比同层的节点，而不是跨层对比  
步骤分为两步：
- 首先从上至下，从左往右遍历对象，也就是树的深度遍历，这一步会将每一个节点添加索引，便于最后渲染差异
- 一旦节点有子元素，就去判断子元素是否有不同

Virtual Dom的算法实现主要是三步
1. 通过js来模拟创建dom对象
2. 把虚拟dom转换成真实dom插入页面中
3. 发生变化时候，比较两颗树的差异，生成差异对象
4. 根据差异对象渲染差异到真实dom

## setState同步？异步？
1. setState只在合成事件（JSX中的onClick、onChange等）和钩子函数中是**异步**的，在原生事件和setTimeout中都是同步的
2. setState的“异步”并不是说内部是由异步代码实现的，其实本身执行的过程和代码都是同步的，只是合成事件和钩子函数的调用顺序在更新之前，导致在合成事件和钩子函数中没法立马拿到更新后的值，当然也可以用setState第二个参数来获得
3. setState的批量更新优化是建立在“异步”（合成事件，钩子函数）上的。在原生时间和setTimeout中不会批量更新，在“异步”中如果对一个值多次进行setState，setState的批量更新策略会对其进行覆盖，取最后一次的执行，如果是同时setState多个不同的值，在更新时会对其进行合并批量更新

```
class App extends React.Component {
  state = { val: 0 }

  componentDidMount() {
    this.setState({ val: this.state.val + 1 })
    console.log(this.state.val)

    this.setState({ val: this.state.val + 1 })
    console.log(this.state.val)

    setTimeout(_ => {
      this.setState({ val: this.state.val + 1 })
      console.log(this.state.val);

      this.setState({ val: this.state.val + 1 })
      console.log(this.state.val)
    }, 0)
  }

  render() {
    return <div>{this.state.val}</div>
  }
}
```
因为在钩子函数里面setState是异步的，所以前两次无法获得val的值，所以都输出0，然后到setTimeout的时候，setState已经更新了，而且因为是批量更新所以只执行最后一次，所以到setTimeout的时候，val是1。因为setTimeout中是同步的，所以第一次是2，第二次是3


# 32. React常见面试题
## 调用setState之后发生了什么
在代码调用setState函数之后，React会将传入的参数对象与组件当前的状态合并，然后触发调和过程（Reconciliation），经过调和过程，React会以相对高效的方式根据新的状态构建React元素树，并且重新渲染整个UI界面。React得到元素树之后，会计算出新树与老树的节点差异，然后根据差异对界面进行最小化的重渲染。在差异算法中，React能够相对精确的知道那些地方发生了改变，这就保证了按需更新，而不是全部重新渲染

## React中Element和Component的区别
React Element是描述屏幕上可见内容的数据结构，是对于UI的对象表述。而React Component这是可以接受参数输入并且返回某个React Element的函数或者类

## 什么情况下你会优先选择使用Class Component而不是Functional Component
当组件需要内部状态以及生命周期函数的时候就选择Class Component，否则就是用Functional Component

## React中refs的作用是什么
Refs是React提供的可以安全访问dom元素或者某个组件实例的句柄，可以为元素添加ref属性然后再回调函数中接受该元素在dom树中的句柄

## React中keys的作用
keys是React用于追踪列表中哪些元素被修改、添加或者删除的辅助标识，需要保证key的唯一性。React diff算法中，会借助key值来判断元素是新建的还是移动而来的，从而减少不必要的元素重渲染。此外React还需要借助Key值来判断元素与状态的关联关系

## 受控组件与非受控组件的区别
- 受控组件指那些将表单数据给React统一管理的组件，需要使用setState来更新表单的值
```
this.state = {
    value: ''
}

...

handleChange = (e) => {
    this.setState({
        value: e.target.value
    })
}

...

<input onChange={() => this.handleChange} />
```

- 非受控组件就是由dom来存放表单数据，我们可以使用refs来操控dom元素
```
handleChange = () => {
    console.log(this.input.value)
}

...

<input refs={(input) => this.input = input}
    onChange={() => this.handleChange} />
```

尽管非受控组件比较容易实现，但是我们有时候会需要对数据进行处理，使用受控组件会更加容易

## 在声明周期中哪一步应该发起Ajax请求
应该放在`componentDidMount()`

- Fiber调和算法会影响到compnentWillMount的触发次数，如果放在里面，可能会发起多次Ajax请求
- 如果放在其他生命周期中，假设我们获取了Ajax请求的结果，并且添加到组件的状态中，未挂载的组件就会报错。而在`componentDidMount`中就不会有这些问题了

## shouldComponentUpdate的作用是什么，为何他如此重要
shouldComponentUpdate允许我们手动的判断组件是否更新，就可以避免不必要的更新渲染

## React中的事件处理逻辑
为了解决跨浏览器兼容性的问题，React会将浏览器原生事件封装为合成事件传入设置的事件处理器中。合成事件与原生时间采用相同的接口，不过他们屏蔽了底层浏览器的细节差异，保证了行为的一致性。React没有将事件依附在子元素上，而是将所有事件发送到顶层 `document` 进行处理

JSX上面的事件全部绑定在 `document` 上，不仅减少了内存消耗，而且组件销毁的时候可以统一移除事件

如果我们不想事件冒泡的话，应该是调用`event.preventDefault`，而不是传统的`event.stopPropagation`

## createElement和cloneElement的区别是什么
createElement函数是JSX编译之后使用的创建Element的函数，而cloneElement这是复制某个元素并传入新的Props

## setState函数的第二个参数的作用是什么
是一个回调函数，这个函数会在setState函数调用完成并且组件开始重渲染的时候被调用，我们可以通过这个函数来判断更新渲染是否完成

## 为什么虚拟dom会提高性能
虚拟dom相当于在js和真实dom中间加了一个缓存，利用dom diff算法避免了没有必要的dom操作，从而提高性能
具体步骤如下：
1. 使用js来模拟创建一个dom
2. 将这个虚拟dom构建真实dom，插入到页面中
3. 状态变更时，比较两颗对象树的差异，生成差异对象
4. 根据差异对象进行更新

## diff算法
- 把树形结构按照层次分解，只比较同级元素  
- 为列表结构的每一个元素都添加唯一的key属性，方便比较
- 如果是同一类型的组件，则按照tree diff一样遍历
- 如果不是同一类，则该组件判断为dirty component，从而替换整个组件下的所有子节点，就不用花时间来比较差异了
- 合并操作，调用setState的时候会将组件标记为dirty，到一个事件循环结束，React检查所有标记dirty的component重新绘制。这样dom只会被更新一次，节约性能
- 选择性子树渲染，利用shouldComponentUpdate来提高diff性能

## diff算法的三种优化策略
1. 树的优化策略
- 层级控制，diff树同层只比较同一层次的节点
- 如果某个节点不存在，则这个节点直接删除
- 跨层级比较会进行相应的创建或者删除

2. 组件的优化策略
- 是否为同一类型，有则使用tree diff
- 不是同一类型，则判断为dirty component。从而替换掉整个组件下的子节点
- 对于同一类型的组件，可以使用shouldComponentUpdate来手动终止diff算法，加快渲染速度

3. 元素的优化策略
- 插入，全新的节点需要执行插入操作
- 移动，节点本身存在，需要进行移动
- 删除，结构相同内容不同，无需直接复用，需要删除重建
- 基于唯一标记key来进行计算，快速定位

## react性能优化
- 利用shouldComponentUpdate来避免不必要的dom操作
- 使用key来帮助React识别列表子组件的最小变化

## 简述Flux思想
Flux最大的特点就是，**数据单向流动**
1. 用户访问View
2. View发出用户的Action
3. Dispatcher收到Action，要求Store进行相应的更新
4. Store更新后，发出一个“change”事件
5. View收到“change”事件后，更新页面

## 展示组件（Presentational component）和容器组件（Container component）之间有何不同
- 展示组件关心组件看起来是什么，专门通过props来接收数据和回调，一般不会有自己的状态
- 容器组件关心组件如何运作，容器组件会为展示组件或者其他容器组件提供数据和行为，一般拥有自己的状态，因为他是其他组件的数据源

## 组件的状态（state）和属性（props）有何区别
- state是一种数据结构，用于组件挂载时所需的数据默认值。一般由用户事件行为改变state
- props是组件的配置，由父组件传给子组件，props不可改变。

## 什么是高阶组件
高阶组件是一个以组件为参数并返回一个新组建的函数。HOC运行重用代码、逻辑和引导抽象。最常见是Redux的connect函数。HOC最好的方式是分享组件之间的行为。如果发现一个地方大量代码用来做一件事情，可以考虑重构为HOC

## 为什么建议setState的参数是一个callback而不是对象
因为state和props的更新可能是异步的，不能依赖他们去计算下一个state

## 除了在构造函数绑定this，还有其他办法吗
在回调中可以使用箭头函数，但是问题就是每次渲染都会创建一个新的回调

## 构造函数中为什么要调用super
因为`super()`被调用之前，子类是不可以使用this的

## React的三种构建组件的方式
React.createClass、ES6 class、无状态函数

## useEffect和useLayoutEffect的区别
调用时间不同
- useEffect是在组件渲染完之后执行
- useLayoutEffect是在组件渲染前就执行

useLayoutEffect比useEffect先执行

## 实现 useState 和 useEffect
> React是使用类似单链表的形式来代替数组，通过next按顺序串联所有hook

useEffect特点：
1. 两个参数：一个回调函数，一个依赖数组
2. 如果依赖数组不存在，则callback每次render都触发
3. 如果依赖数组存在，只有他发生改变的时候才执行callback

![image](https://pic4.zhimg.com/80/v2-ed25525d8a2985c3fd6d599050df5a83_hd.jpg)

```javascript
let arr = [] // 一个数组，存储每一个hook
let index = 0 // 下标，存取每个hook对应的位置

function useState(init){
    arr[index] = arr[index] || init // 如果存在则用之前的值
    const cur = index // 设置一个变量存储当前下标
    
    function setState(newState){
        arr[cur] = newState
        render() // 渲染，页面触发更新
    }
    
    return [arr[index++], setState]
}

function useEffect(callback, deps){
    const hasNoDeps = !deps // 如果没有依赖，则直接每次更新
    const lastDeps = arr[index] // 获取上一次的依赖数组
    const hasChangeDeps = lastDeps
      ? !deps.every((e, i) => e === lastDeps[i]) // 如果每一项都相同
      : true
    if(hasNoDeps || hasChangeDeps){
        callback()
        arr[index] = deps
    }
    index++
}
```

## React新特性
1. Lazy 和 Supense
```
import React, {Component, lazy, Suspense} from 'react'

const About = lazy(() => import(/*webpackChunkName: "about" */'./About.jsx'))

class App extends Component {
  render() {
    return (
      <div>
        // 我们需要用suspense来进行过渡，显示一个loading
        <Suspense fallback={<div>Loading...</div>}>
          <About></About>
        </Suspense>
        
        // 这样子是不行的，因为还没有加载完成不知道显示什么
        <!--<About></About>-->
      </div>
    );
  }
}

export default App;
```

2. 错误边界（Error boundaries）
```
class App extends Component {
  state = {
    hasError: false,
  }
  static getDerivedStateFromError(e) {
    return { hasError: true };
  }
  render() {
    if (this.state.hasError) {
      return <div>error</div>
    }
    return (
      <div>
        <Suspense fallback={<div>Loading...</div>}>
          <About></About>
        </Suspense>
      </div>
    );
  }
}
```

3. React.memo
React.memo适用于函数组件，不适用于class组件

与`pureComponent`类似，但是`pureComponent`提供的`shouldComponentUpdate`只是对比传入的props本身有没有变化，如果内部的值变了，他也不会更新。例如
```
class Foo extends PureComponent {
  render () {
    console.log('Foo render');
    return <div>{this.props.person.age}</div>;
  }
}

person: {
  count: 0,
  age: 1
}

// person.age++, 本来应该触发更新，但是不会因为props的第一级没有发生变化
```

这时候我们可以用memo来优化一下
```
const Foo = memo(function Foo (props) {
  console.log('Foo render');
  return <div>{props.person.age}</div>;
})
```
memo的第一个参数是函数组件，第二个是与`shouldComponentUpdate类似`是一个函数
```
(nextProps, nextState)=>{
    
}
```

4. hook的优势
- 函数组件没有this的问题
- 自定义hook方便复用状态逻辑
- 副作用关注点分离


## React 状态提升
常见于子组件的数据存在父组件中
```
// 父组件
class AllInput extends React.Component {
    constructor(props) {
        super(props)
        this.state = { content: '' }
        this.handleContentChange = this.handleContentChange.bind(this)
    }
    handleContentChange(newContent) {
        this.setState({ content: newContent })
    }
    
    render() {
        return (
            <div>
                <Input content={ this.state.content } onContentChange={ this.handleContentChange }/>
                <br /><br />
                <Input content={ this.state.content } onContentChange={ this.handleContentChange }/>
            </div>
        )
    }
}


// 子组件
class Input extends React.Component {
    constructor(props) {
        super(props)
        this.handleChange = this.handleChange.bind(this)
    }

    handleChange(e) { 
        setState（修改数据的方法）
        this.props.onContentChange(e.target.value)
    }

    render() {
        return (
            <input type='text' value={ this.props.content } onChange={ this.handleChange } />
        )
    }
}
```

## 高阶函数
> 高阶函数就是接受一个或者多个函数然后返回一个函数的东西

主要功能有两个
### 属性代理
属性代理有三个常用的作用

- 操作props

```
function HigherOrderComponent(WrappedComponent) {
    return class extends React.Component {
        render() {
            const newProps = {
                name: '大板栗',
                age: 18,
            };
            return <WrappedComponent {...this.props} {...newProps} />;
        }
    };
}
```
这样子，就可以将自定义的props传给子组件了

- 抽离state
```
// 普通组件Login
import React, { Component } from 'react';
import formCreate from './form-create';

@formCreate
export default class Login extends Component {
  render() {
    return (
      <div>
        <div>
          <label id="username">
            账户
          </label>
          <input name="username" {...this.props.getField('username')}/>
        </div>
        <div>
          <label id="password">
            密码
          </label>
          <input name="password" {...this.props.getField('password')}/>
        </div>
        <div onClick={this.props.handleSubmit}>提交</div>
        <div>other content</div>
      </div>
    )
  }
}

//HOC
import React, { Component } from 'react';

const formCreate = WrappedComponent => class extends Component {

  constructor() {
    super();
    this.state = {
      fields: {},
    }
  }
  onChange = key => e => {
    const { fields } = this.state;
    fields[key] = e.target.value;
    this.setState({
      fields,
    })
  }
  handleSubmit = () => {
    console.log(this.state.fields);
  }
  getField = fieldName => {
    return {
      onChange: this.onChange(fieldName),
    }
  }
  render() {
    const props = {
      ...this.props,
      handleSubmit: this.handleSubmit,
      getField: this.getField,
    }
    return (<WrappedComponent
      {...props}
    />);
  }
};
export default formCreate;
```
例如这样，就可以将输入框的state抽离出来

- 操作refs
```
import React, { Component } from 'react';

const refHoc = WrappedComponent => class extends Component {

  componentDidMount() {
    console.log(this.instanceComponent, 'instanceComponent');
  }

  render() {
    return (<WrappedComponent
      {...this.props}
      ref={instanceComponent => this.instanceComponent = instanceComponent}
    />);
  }
};

export default refHoc;
```
这样就可以获取组件的示例了  
**不可以再无状态组件（函数类型组件）上使用`refs`，因为无状态组件没有实例**

### 反向继承
```
function HigherOrderComponent(WrappedComponent) {
    return class extends WrappedComponent {
        render() {
            return super.render();
        }
    };
}
```
反向继承就是一个函数接收一个组件作为参数传入，然后返回一个继承该组件的类，在该类的`render`里面调用`super.render()`

- 可以操作state，但是会难以维护
- 渲染劫持

渲染劫持我们可以控制组件的render，有条件的展示组件
例如
1. 条件渲染
```
function withLoading(WrappedComponent) {
    return class extends WrappedComponent {
        render() {
            if(this.props.isLoading) {
                return <Loading />;
            } else {
                return super.render();
            }
        }
    };
}
```
这样就可以按条件来控制组件渲染了

2. 修改render输出
```
  //hijack-hoc
  import React from 'react';

  const hijackRenderHoc = config => WrappedComponent => class extends WrappedComponent {
    render() {
      const { style = {} } = config;
      const elementsTree = super.render();
      console.log(elementsTree, 'elementsTree');
      if (config.type === 'add-style') {
        return <div style={{...style}}>
          {elementsTree}
        </div>;
      }
      return elementsTree;
    }
  };

  export default hijackRenderHoc;
  
  //usual
  @hijackRenderHoc({type: 'add-style', style: { color: 'red'}})
  class Usual extends Component {
    ...
  }
```

## HOC存在的问题
- 静态方法丢失
- refs属性不能透传
- 反向继承不能保证子组件完整被解析

## HOC约定
- props保持一致
- 不能再函数式（无状态）组件中使用refs，因为他没有
- 不要改变子组件
- 可以添加包装名便于调试
- render里不要使用HOC

## 应用场景
1. 权限控制
2. 页面复用


# 33. CSRF 和 XSS
## 区别
- CSRF需要登录之后操作，XSS不需要
- CSRF是请求页面api来实现非法操作，XSS是向当前页面植入js脚本来修改页面内容

## CSRF
跨站点伪造请求  
用户在一个网站登录之后，产生一个cookie，此时若打开了一个新的网址，此网址返回了一些恶意的请求，就属于CSRF攻击

- 预防
1. 验证http reference
2. 请求地址中添加token验证
3. 请求头中添加token验证

## XSS
跨站脚本攻击，一般是通过web页面插入恶意js代码来攻击。
主要分为三类：
1. 反射性: xss代码在请求url中攻击
2. 存储型: 将攻击脚本存入服务端，从而传播
3. dom型: 通过dom修改页面内容

- 预防
1. 输入过滤: 例如过滤`<script>`等
2. 输出转义: 例如将`<`,`>`,`/`等字符利用转义符号转换一下
3. 使用httponly: 让js脚本无法访问cookie
4. 尽量使用post方法，使用get的时候限制一下长度

## 总结
- 加入token是为了防止CSRF的而不是XSS
- CSRF的攻击是因为浏览器自动带上cookie，而不会自带token

# 34. localStorage 和 sessionStorage 和 cookie
## localStorage
生命周期是永久，只能存字符串类型
- 跨域
使用iframe与postMessage实现

## sessionStorage
生命周期为，当前窗口或标签页未被关闭，一旦关闭则存储的数据全部清空

## cookie
cookie生命周期在过期时间之前都有效，同浏览器下，所有同源窗口之间共享

cookie的属性
- name: 必须，定义cookie的名称
- value: 必须，指定cookie的值
- expires: 指定过期时间，采用UTC或GMT格式，如果不设置cookie只会在当前会话（session）有效，浏览器窗口关闭cookie就会删除
- domain: 指定cookie所在域名，默认为设定cookie时候的域名，所指定的域名必须是当前发送cookie的一部分，只有访问的域名匹配domain属性，cookie才会发送
- path: 指定路径，必须是绝对路径，默认为请求该cookie的网页路径，只有path属性匹配向服务器发送的路径，cookie才会发送，只要path属性匹配发送路径的一部分就可以了，例如`path=/blog`，发送的路径是`/blogroll`也可以。path属性生效的前提是domain属性匹配
- secure: 指定cookie只能在加密协议https下发送到服务器，如果通信是https协议，自动打开
- max-age: 用来指定cookie有效期，max-age优先级高于expires
- httponly: httponly属性用于设置该cookie不能被JavaScript访问，主要是为了防止xss工具盗取cookie


## 总结
- 不同浏览器无法共享localStorage和sessionStorage
- 相同浏览器不同页面之间可以共享相同的localStorage（页面属于相同域名和端口）
- 相同浏览器不同标签页中无法共享sessionStorage的信息

# 35. BFC 及其作用
BFC就是格式化上下文，相当于一个容器，里面的元素和外部相互不影响，创建的方式有：
1. html根元素
2. float浮动
3. 绝对定位元素position: fixed || absolute
4. overflow不为visiable
5. display为table、inline-block、flex

BFC主要的作用是
1. 清除浮动
2. 防止同一个BFC中相邻元素间的外边距重合
3. BFC元素和浮动元素不会重叠
4. BFC在计算高度时会把浮动元素也计算进去

# 36. 实现 (5).add(3).minus(2) 功能
```
Number.prototype.add = function(n) {
  return this + n;
};
Number.prototype.minus = function(n) {
  return this - n;
};
```

# 37. 连续赋值
例1：
```
var a = 3;
var b = a = 5;

=

var a = 3
var a = 5
var b = a
```
所以最后a和b都是5

例2：
```
var a = { n: 1 }
var b = a

a.x = a = { n: 2 }
```
一开始a和b都引用对象`{n:1}`，然后到赋值语句  
如果赋值语句中出现`.`则他会比`=`先一步执行，也就是说，我们先给a.x开辟一个空间  
也就是说现在的a和b都是变成了
```
{
  n: 1,
  x: {
      n: 2
  }
}
```
接下来到a的赋值了，a现在就变成了
```
{
    n: 2
}
```

# 38. display: none, visibility: hidden 和 opacity: 0
- `display: none`: 不占空间，不能点击，一般用于隐藏元素，会引发回流，性能开销大，非继承属性，子孙节点改变也无法显示（父元素为none）
- `visibility: hidden`: 占据空间，不能点击，显示不会导致页面结构变化，不会撑开，属于重绘操作，是继承属性，子孙节点可以通过修改显示出来
- `opacity: 0`: 占据空间，可以点击，一般与transition一起用

# 39. for 和 forEach 的性能
for 比 forEact 快
因为
- for没有额外的函数调用栈，和上下文

# 40. react-router的`<Link>` 和 `<a>` 有何区别
<Link>是禁用了<a>标签的默认事件，他只会更新匹配的页面的内容，而不会刷新整个页面。他使用的是`history`来进行跳转，会改变url，但是不会刷新页面

# 41. 执行上下文
- **全局执行上下文**：默认的上下文，任何不在函数内部的代码都在全局上下文里面。他会执行两件事情： 创建一个全局的window对象，并且设置this为这个全局对象。一个程序只有一个全局对象
- **函数执行上下文**：每当一个函数被调用，就会为该函数创建一个新的上下文，每个函数都有自己的上下文，不过是在函数被调用的时候创建的。函数上下文可以有任意多个，每当一个新的执行上下文被创建，他会按照定义的顺序执行一系列的步骤
- **Eval函数执行上下文**：执行在`eval`函数内部的代码有他自己的执行上下文

# 42. 执行栈
执行栈就是一个调用栈，是一个后进先出数据结构的栈，用来存储代码运行时创建的执行上下文
```
let a = 'Hello World!';

function first() {
  console.log('Inside first function');
  second();
  console.log('Again inside first function');
}

function second() {
  console.log('Inside second function');
}

first();
console.log('Inside Global Execution Context');
```
![image](https://user-gold-cdn.xitu.io/2018/9/20/165f539572076fe3?imageView2/0/w/1280/h/960/format/webp/ignore-error/1)

# 43. 创建执行上下文
分为两个阶段
- 创建阶段
- 执行阶段

## 创建阶段
代码执行前会创建执行上下文，会发生三件事
1. this绑定
2. 创建词法环境组件
3. 创建变量环境组件

### this绑定
全局执行上下文中，this指向全局对象

函数执行上下文中，this取决于函数是如何被调用的。如果他被一个引用对象调动，那么this会设置成那个对象。否则是全局对象
```
let foo = {
  baz: function() {
  console.log(this);
  }
}

foo.baz();   // 'this' 引用 'foo', 因为 'baz' 被
             // 对象 'foo' 调用

let bar = foo.baz;

bar();       // 'this' 指向全局 window 对象，因为
             // 没有指定引用对象
```

### 词法环境
是一个用代码的词法嵌套结构定义标识符和具体变量和函数关联的东西。用来存储函数声明和`let`, `const`声明的变量绑定

### 变量环境
同样是一个词法环境，用来存储`var`变量绑定
```
let a = 20;
const b = 30;
var c;

function multiply(e, f) {
 var g = 20;
 return e * f * g;
}

c = multiply(20, 30);
```
只有在调用函数multipy的时候才会创建函数执行上下文，let和const一开始不会关联任何值，但是var已经会设置为undefined了，这就是常说的**变量声明提升**

# 44. 事件循环
任务分为两类
- 同步任务
- 异步任务

![image](https://user-gold-cdn.xitu.io/2017/11/21/15fdd88994142347?imageView2/0/w/1280/h/960/format/webp/ignore-error/1)

宏任务
- 主体代码
- setTimeout
- setInterval
- setImmediate
- requestAnimationFrame

微任务
- process.nextTick
- mutation.observer
- Promise.then cath finally

# 45. link 与 @import
- link属于html标签，@import属于css提供的
- 页面加载的时候link就加载，而@import是等页面加载完成之后再加载css
- link不存在兼容性问题
- link权重更大

# 46. 外边距重叠
- 两个相邻的外边距都是正数时，折叠效果是两者之间较大的
- 两个相邻的外边距都是负数时，折叠效果是绝对值最大的
- 两个外边距一正一负时候，效果是相加起来

# 47. 渐进增强 和 优雅改进
- **渐进增强**：针对低版本浏览器进行构建页面，保证最基本的功能，然后再针对高级浏览器进行效果、交互等改进
- **优雅改进**：一开始就构建好完整的功能，然后再对低版本浏览器进行兼容

区别：渐进增强是向上兼容，优雅改进是向下兼容

# 48. 立即执行函数
作用
- 不破坏全局的命名空间
- 如需使用，要将变量传入

```
(function(x){
  console.log(x);
}(12345))
```

# 49. HTTP2.0 与 HTTP1.1
## HTTP2.0
1. HTTP2.0基本单位为二进制，以往是采用文本形式，健壮性不是很好，现在采用二进制格式，更方便更健壮
2. HTTP2.0的多路复用，把多个请求当做多个流，请求响应数据分成多个帧，不同流中的帧交错发送，解决了TCP连接数量多，TCP连接慢，所以对于同一个域名只用创建一个连接就可以了
4. HTTP2.0压缩消息头，避免了重复请求头的传输，又减少了传输的大小
5. HTTP2.0服务端推送，浏览器发送请求后，服务端会主动发送与这个请求相关的资源，之后浏览器就不用再次发送后续的请求了。
6. HTTP2.0可以设置请求优先级，可以按照优先级来解决阻塞的问题

## HTTP1.1
- 缓存处理新增etag、if-none-match之类的缓存头来控制缓存
- 长连接，可以在TCP连接上发送多个请求和响应



# 50. css动画与js动画的区别
- css性能好
- css代码逻辑相对简单
- js动画控制好
- js动画兼容性好
- js可以实现动画多
- js可以添加事件

# 51. offset、client和scroll的属性
- client：padding + content - 滚动条
- offset：padding + content + boder
- scroll：padding + 实际的content

# 52. 手撕代码题
1. 输入根节点，打印标签路径，以及路径上data-v最大值
```
const root = document.getElementById("root");

function walk(node, path, max) {
  if (!node) {
    return;
  }
  path = [...path, node.tagName];
  max = Math.max(max, node.dataset.v);
  console.log(path, max);
  for (let child of node.children) {
    walk(child, path, max);
  }
}
walk(root, [], -1)

...

<div id="root" data-v="3">
  <p data-v="1">p1</p>
  <span data-v="2">
    span1
    <span data-v="4">span2</span>
    <span data-v="5">
      <p>1</p>
    </span>
  </span>
  <p data-v="99">p2</p>
</div>
```


2. 实现compose函数
```
var arr = [func1, func2, func3];
function func1(ctx, next) {
  ctx.index++
  next();
}
function func2(ctx, next) {
  setTimeout(function () {
    ctx.index++
    next();
  });
}
function func3(ctx, next) {
  console.log(ctx.index);
}

compose(arr)({ index: 0 });

function compose(arr) {
  return function (ctx) {
    if (arr.length !== 0) {
      let func = arr.shift()
      func(ctx, next)
    }
    function next() {
      if (arr.length !== 0) {
        let func = arr.shift()
        func(ctx, next)
      }
    }
  }
}
```



# 53. 行内元素的margin 和 padding
- **水平方向**：水平方向上，都有效
- **垂直方向**：垂直方向上，都无效，但是padding-bottom, padding-top会显示出效果，但是高度不会撑开，不会对周围元素有影响

# 54. 行内元素和块级元素
- 行内、块级元素可以相互转换
- 行内元素会在一条水平线上排列，块级则会在新的一行
- 行内元素不可以设置宽高，但是可以设置行高（line-height）
- 行内元素垂直方向上设置margin和padding无效，padding垂直方向有显示但是不会撑开，不会影响别的元素
- 块级可以包含行内元素和块级元素，行内元素只可以包含行内元素和文本


# 55. margin、padding和translate百分比是按照什么计算的
- margin：按照父元素的宽来计算的
- padding：按照父元素的宽来计算的
- translate：是按照本身的宽���计算的


# 56. display: inline-block元素之间有间隙
**原因**
`inline-block`对外是`inline`，对内是`block`，会将连续的空白符解析为一个空格

**解决办法**
- 删除空格
- 父元素设置`font-size: 0`
- 父元素设置`letter-spacing: -4px`
- 子元素设置`vertical-align: bottom`去除垂直间隙

# 57. HTTPS原理
HTTP是明文传输，传输的每一个环节都可能会被第三方窃取或者篡改。具体来说就是HTTP数据经过TCP层，然后经过WIFI路由器、运营商和目标服务器，都可能被中间人拿到数据并进行篡改，这就是常说的**中间人攻击**

HTTPS是一个加强版的HTTP。采用**对称加密**和**非对称加密**结合的方式来保护浏览器和服务端之间的通信安全。
对称加密算法加密数据 + 非对称加密算法交换密钥 + 数字证书验证身份 = 安全

HTTPS由两部分组成：HTTP + SSL/TLS，也就是在HTTP上又加了一层处理加密信息的模块。服务端和客户端的信息传输都会通过TLS进行加密，所以传输的数据是加密后的数据

## 加密过程
首先浏览器会给服务器发送一个`client_random`和一个加密的方法列表  

服务器接受后给浏览器返回另一个随机数`server_random`和加密方法  

现在两者拥有三种相同的凭证: `client_random`, `server_random`和`加密方法`  

接着用这个加密方法将两个随机数混合起来生成密钥，这个密钥就是浏览器和服务器通信的`暗号`了


## 对称加密和非对称加密
- 对称加密是最简单的方式，指的是加密和解密用的是同样的秘钥，优点是保证了消息的保密性，但缺点是密钥可能会泄露

- 非对称加密是说，如果有A、B两把密钥，用A加密过的数据包只能用B解密，反之用B加密的数据包只能由A解密，客户端在发消息的时候，先用公钥加密，服务器再用私钥解密。但是因为公钥不是保密的，可能会被窃取然后对消息进行篡改

## 数字证书和数字签名
为了解决非对称加密中公匙来源的不安全性。我们可以使用数字证书和数字签名来解决。

首先本地生成一对密钥，通过公钥去CA申请数字证书

- **数字签名**：CA拿到信息后会通过单向的hash算法把信息加密，然后生成一个摘要，然后CA会用自己的私钥对摘要进行加密，最后得出的结果就是数字签名了
![image](https://user-gold-cdn.xitu.io/2017/10/16/6efb9ac7ac6baa22cd88fd35074f46b7?imageView2/0/w/1280/h/960/format/webp/ignore-error/1)

- **数字证书**：最后CA会将申请的信息还有数字签名整合在一起，就生成了数字证书了，其实也就是一个公钥
![image](https://user-gold-cdn.xitu.io/2017/10/16/808f41fbb63ec6f3397288368160c7a6?imageView2/0/w/1280/h/960/format/webp/ignore-error/1)

- **数字证书如何起作用**：
1. 客户端用CA的公钥解密数字证书，如果数字证书来源合法，解密成功后，客户端就获得了信息摘要了。然后客户端会按照和CA一样的hash算法将申请信息生成一份摘要。
2. 然后和解密出来的那份摘要进行对比，如果内容完整，则说明没有被篡改。客户端就可以从证书中拿到服务器的公钥和服务器进行安全的非对称加密通信了。服务器要想获得客户端的公钥也可以通过这个方式

## 握手过程
1. 客户端申请https通信
2. 服务器响应然后向客户端发送数字证书（公钥）
3. 客户端TLS验证证书，拿到公钥，如果没有问题就生成一个随机值，然后用公钥加密传给服务器
4. 服务器收到后用私钥解密，拿到了对称密钥，之后可以通过这个密钥进行信息传输了，然后建立SSL连接通道
5. 共享密钥交换成功，客户端和服务端开始加密通信
6. 断开连接
![image](https://user-gold-cdn.xitu.io/2017/10/16/be5e7b8e6b17fed4edf31dbf4ee65117?imageView2/0/w/1280/h/960/format/webp/ignore-error/1)

```
客户端: 你好，我要发起一个 HTTPS 请求，请给我公钥
服务器: 好的，这是我的证书，里面有加密后的公钥
客户端: 解密成功以后告诉服务器: 这是我的 (用公钥加密后的) 对称秘钥。
服务器: 好的，我知道你的秘钥了，后续就用它传输。
```

## 使用
https加解密耗时比较长，也很消耗资源，如果不是安全性要求非常高可以不用

# 58. setImmediate() 和 process.nextTick()
- setTimeout为在指定时间之后就执行
- setImmediate设计是当前轮询阶段完成后就立即执行
如果放在同一个I/O循环内使用，setImmediate总是被优先调用，他的优势是如果在I/O周期内被调度的话，他会在所有定时器之前执行。他执行的方式是当前任务队列的尾部
- process.nextTick触发的是在当前执行栈的尾部，下一次事件循环之前，总是在异步之前。

为什么要使用process.nextTick()，因为可以允许用户处理错误，或者是在事件循环继续之前重试请求


# 59. 浏览器和node的事件循环
浏览器任务分为**宏任务**和**微任务**
- 宏任务：script中的代码、setTimeout、setInterval、I/O、UI render
- 微任务：promise、Object.observe、MutationObserver

node分为以下几种：
- microTask：微任务
- nextTick：process.nextTick
- timers: 各类定时器
- I/O callback：是否有已完成的I/O操作的回调函数，来自上一轮的轮训的残留，执行几乎所有的回调，但是不包括close，定时器还有setImmediate
- idle，prepare：仅在内部使用
- poll：等待新的I/O事件，会因timers和超时事件等结束时间，一般阻塞在这里
- check：执行setImmediate的回调
- close callback：关闭所有的closing handles，一些onclose事件

## Node环境下
循环之前，会执行以下操作：
- 同步任务
- 发出异步请求
- 规划定时器生效的时间
- 执行process.nextTick()

开始循环
循环中进行的操作：
- 清空timers队列，清空nextTick队列，清空microTask队列
- 清空I/O队列，清空nextTick队列，清空microTask队列
- 清空check队列，清空nextTick队列，清空microTask队列
- 清空close队列，清空nextTick队列，清空microTask队列

![image](https://image.fundebug.com/2019-01-14-005.png)

## 区别
- node环境下的setTimeout定时器会依次一起执行，浏览器是一个一个分开的
- 浏览器环境下微任务的执行是每个宏任务执行之后，而node中微任务会在各个阶段之间执行，一个阶段结束立刻执行mircroTask

## 总结
浏览器环境下：
```
while(true){
    宏任务队列.shift()
    微任务队列全部任务()
}
```

Node环境下：
```
while(true){
    loop.forEach((阶段)=>{
        阶段全部任务()
        nextTick全部任务()
        microTask全部任务()
    })
}
```


# 60. React Fiber
原先React采用的是**stack reconciler**调度算法。页面可能会出现卡顿，因为setState之后React会立即开始调和过程，会遍历找不同，所有virtual dom都遍历完之后，才会渲染。在调和的过程时候，主线程被js占用了，所以交互、布局都会停止，就会卡顿

所以现在采用了Fiber reconciler来优化
- 任务拆分
- 更新暂停，终止和复用
- 设置优先级
- render可以返回多个元素

## Scheduler
调度是fiber调和的一个过程

如果UI要有不错的表现，那就得考虑多点东西
- 并不是所有state都需要立刻更新，例如不在可视范围内的
- 不是所有更新优先级都是一样的，例如用户输入的优先级比请求资源展示要高
- 高优先级的应该打断低优先级的更新

所以调和的过程是每次只做一个小小的任务，完成之后查看还有没有优先级高的任务需要处理

## Fiber数据结构
![image](https://pic2.zhimg.com/80/v2-453e1f48a4f53356bee021c90ee00bed_hd.jpg)
- return: 父节点
- child：第一个子节点
- sibling：兄弟节点

```
fiber {
  	stateNode: {},
    child: {},
    return: {},
    sibling: {},
}
```

## 任务拆分
Fiber拆分的单位是按照虚拟dom节点来拆，因为fiber tree是根据虚拟dom来构造出来的

## 任务暂停
Fiber利用浏览器的api`requestIdleCallback`来让浏览器空闲的时候执行某种任务
```
function fiber(剩余时间) {
 if (剩余时间 > 任务所需时间) {
 做任务;
 } else {
 requestIdleCallback(fiber);
 }
}
```

使用`requestAnimationFrame`来渲染动画

## 优先级
```
{ 
 Synchronous: 1, // 同步任务，优先级最高
 Task: 2, // 当前调度正执行的任务
 Animation 3, // 动画
 High: 4, // 高优先级
 Low: 5, // 低优先级
 Offscreen: 6, // 当前屏幕外的更新，优先级最低
}
```


# 61. webpack流程
1. 初始化：从配置文件读取与合并参数，然后实例化插件`new Plugin()`
2. 开始编译：通过上一步获取的参数，初始化一个`Complier`对象加载插件，执行`Compiler.run`开始编译
3. 确定入口：根据配置中`entry`找出所有入口文件
4. 编译模块：从`entry`出发，调用配置的`loader`，对模块进行转换，同时找出模块依赖的模块，一直递归，一直到找到所有依赖的模块
5. 完成模块编译：这一步已经使用`loader`对所有模块进行了转换，得到了转换后的新内容以及依赖关系
6. 输出资源：根据入口与模块之间的依赖关系，组装成`chunk`代码块，生成文件输出列表
7. 输出成功：根据配置中的输出路径还有文件名，把文件写入系统，完成构建

# 62. webpack的热更新
主要依赖`webpack`, `express`, `websocket`
- 使用`express`启动本地服务，当浏览器访问的时候做出相应
- 服务端和客户端使用`websocket`实现长连接
- `webpack`监听源文件的变化
    - 每次编译完成之后会生成**hash**值，已改动模块的json文件，已改动模块代码的js文件
    - 编译完成后通过`socket`向客户端推送当前编译的hash值
- 客户端的`websocket`监听到有文件改动推送过来的hash值，会和上一次进行对比
    - 一致就走缓存
    - 不一致则通过ajax和jsonp获取最新的资源
- 使用内存文件系统去替换有修改的内容实现局部更新


# 63. CommonJs 与 ES6模块化区别
- CommonJs支持动态导入，ES6不支持
- CommonJs是同步导入，ES6是异步导入
- CommonJs导入的时候是值拷贝，如果导出变了他也不会变，但是ES6是引用的，如果导出变了，导入的部分也会变了

用法
- 导出：CommonJs是`module.exports`，ES6是`export / export default`
- 导入：CommonJs是`const x = require('xx')`，ES6是`import xx from 'xxx'`


# 64. 箭头函数和普通函数
普通函数
- 一般this指向全局对象window
- 作为对象方法调用的时候，this指向对象
- 作为构造函数时候，this指代new的对象
- 可以通过call、apply来改变this

箭头函数
- this总是指向词法作用域
- 无法通过call、apply改变this


# 65. node读取文件转换为buffer
```javascript
const fs = require('fs')
const path = require('path')
const mimeType = require('mime-types') // 文件类型

const filePath = path.resolve('./01.png')
const data = fs.readFileSync(filePath)
const buffer = new Buffer(data).toString('base64')
const base64 = `data:${mimeType.lookup(filePath)};base64,${buffer}`
console.log(base64)

```

# 66. sort函数
- 数量小于10的数组使用插入排序
- 数量大于10的数组使用快排

# 67. 闭包 和 自执行函数
## 闭包
优点
- 可以将局部变量一直存在内存中
- 可以避免使用全局变量

缺点：
- 占用内存变多，可能导致内存泄漏

## 自执行函数
- 避免作用域命名污染
- 提升性能，减少对作用域的查找
- 避免全局命名冲突
- 保存闭包状态


## 区别
- 立即执行函数声明完立刻执行，一般只用于一次
- 闭包主要是为了让外部函数可以访问内部变量，减少了全局变量的使用

# 68. 0.1 + 0.2 ！== 0.3
js采用IEEE 754的双精度标准来进行计算，如果他碰到无法整除的小数的时候，就会取一个近似值，如果足够接近就觉得是那个值了


# 69. React服务端渲染
服务端渲染就是React通过Node.js转换成HTML再返回给浏览器，这个过程被称为“同构”，因为应用程序的大部分代码都可以在服务器和客户端上运行

## 优点
与传统的SPA单页应用程序比，
- 更好的SEO，因为搜索引擎等爬虫工具可以直接查看完全渲染的页面
- 更好的用户体验，如果网络缓慢，或者运行缓慢的设备，服务器渲染就很好

## 弊端
- 由于浏览器跟服务端有区别，document，window等可能获取不了，会报错
- 服务器会占用更多的内存

# 70. 前端路由的原理
- hash模式，后面带了个#，无论hash值怎么变，服务端都只会收到#号前的url
- history模式，主要使用history.pushState和history.replaceState来改变URL，改变url只会更新浏览器的历史记录，不会引起页面更新

hash模式不需要后端配置，兼容性好，history模式需要后端配置才能使用


# 71. Mobx原理
![image](https://upload-images.jianshu.io/upload_images/1935872-a178011f056dd088.png)
特点：
- 开发难度低
- 代码量少
- 渲染性能好

## 工作原理
1. 定义状态让他变成**可观察**的
2. 创建衍生来响应状态变化
3. 使用action来改变状态

## 设计原则
Mobx支持单向数据流，动作改变状态，状态更新改变视图

- Mobx通过不缓存数据，在需要的时候重新计算来保证所有衍生在一致的状态
- 没有参与反应的衍生，就会被简单的垃圾回收

Mobx是同步运行的，有2个好处
- 不会获得旧的衍生
- 追踪堆栈会更简单


# 72. Object.create()实现原理
其实就是新建一个对象，然后覆盖对象的原型为传入的原型对象(类似继承)
```javascript
function(constructor){
    const F = function(){}
    F.prototype = constructor
    const res = new F()
    return res
}
```


# 73. 事件穿透
设置css3属性`pointer-events: none`


# 74. 常见http状态码
- 200：成功，正常处理并返回
- 204：处理成功，但是返回的主体信息没有内容
- 301：永久重定向，请求的资源分配给另一个url
- 302：临时重定向，希望本次访问可以通过另一个url来获取资源
- 303：应该使用get来访问另一个url
- 304：表示协商缓存可用
- 400：请求中有语法错误
- 401：未经许可，要验证
- 403：拒绝访问，权限不够
- 404：访问资源不存在
- 500：请求异常，也可能是前端bug
- 503：服务器停机维护，无法处理请求


# 75. js、css阻塞
js的async加载还有defer加载都不阻塞页面渲染还有资源加载
- defer会按顺序加载，async乱序
- defer是页面都解析完了在运行，立即下载延迟执行
- async下载完成后立刻执行
- 同时指定的话，async优先级高


## 内嵌和外部js
- 内嵌js会阻塞所有资源的加载
- 外部js会阻塞后面的内容呈现以及资源的下载

## css
- css不会阻塞dom解析，会阻塞渲染，因为要dom树跟style树结合生成渲染树才会渲染
- css会阻塞后续js语句执行

> 如果css后面跟着内嵌js，则会出现阻塞情况，因为浏览器会维持css跟js顺序，样式表必须在嵌入的js之前加载完。

# 76. 隐式转换
- 数字运算符
- 点号操作符
- if语句内
- = =

> https://blog.csdn.net/itcast_cn/article/details/82887895

# 77. React首屏优化
1. 使用浏览器缓存
2. webpack的JS压缩，html压缩
3. 提取公共资源
4. 将webpack开发环境修改为生产环境
5. 使用雪碧图
6. 使用cdn

# 78. Object.assign
如果对象只有一层，则是深拷贝，如果是多层则是浅拷贝
```
const obj1 = {
  a: 1,
  b: {
    c: 2
  }
}

const obj2 = Object.assign({}, obj1)
console.log(obj1 == obj2)
console.log(obj1, obj2)
obj1.b = 2
console.log(obj1 == obj2)
console.log(obj1, obj2)
```


# 79. innerHtml 和 outerHtml
![image](http://www.blogjava.net/images/blogjava_net/sxyx2008/69d02044-6eae-397e-a97d-8736d6351d3b.gif)
- inner只是标签内，outer是包括标签


# 80. rem 和 em
- rem是根据根元素的字体大小定的
- em是根据自身元素的字体大小定的，如果自身没有，那可以从父元素继承字体大小


# 81. 垃圾回收机制 和 内存泄漏
## 垃圾回收
- 标记清除

最常用的垃圾回收方式，运行的时候他会给变量标记，如果环境中的变量已经无法访问到这些变量，就清除
```
var m = 0,n = 19 // 把 m,n,add() 标记为进入环境。
add(m, n) // 把 a, b, c标记为进入环境。
console.log(n) // a,b,c标记为离开环境，等待垃圾回收。
function add(a, b) {
  a++
  var c = a + b
  return c
}
```
例如函数的局部变量和参数，外部访问不了，则就会被清除

- 引用计数

判断资源被引用的次数
```
var arr = [1, 2, 3, 4];
arr = [2, 4, 5]
```
例如一开始`[1,2,3,4]`的引用次数为1，不会被清除，但是下面吧arr的引用换了，`[1,2,3,4]`的引用数变成0，将被清除

## 内存泄漏
1. 意外的全局变量
```
function foo(arg) {
    bar = "this is a hidden global variable";
}
```
这样子bar会声明在全局变量里面，不会被释放

2. 计时器
如果使用`setInterval`而没有关闭，则他会一直存在不会被释放

3. 闭包
闭包会维持局部变量，就无法释放了

4. 没有清理dom引用
dom元素的引用如果不清除，他就会一直存在

## 优化
1. 数组优化
```
var arr = [1,2,3]
arr.length = 0 // 这样子优化可以不用新生成一个空数组
```

2. 对象复用
```
var t = {}

while(){
    t.a = 1
}

t = null
```
尽量复用对象不要每次都生成，然后吼用完设置为null，垃圾回收

3. 循环使用函数表达式
```
function t(){
    
}

while(){
    t()
    // var t = function(){} 这样子就不用循环创建很多函数了
}
```

# 82. 手写Promise 和 Promise.all

## Promise
> https://juejin.im/post/5b2f02cd5188252b937548ab

以下为简略版
```javascript
function myPromise(executor) {
  this.state = 'pending';
  this.value = undefined;
  this.reason = undefined;
  this.onResolvedCallbacks = [];
  this.onRejectedCallbacks = [];
  let resolve = value => {
    if (this.state === 'pending') {
      this.state = 'fulfilled';
      this.value = value;
      this.onResolvedCallbacks.forEach(fn => fn());
    }
  };
  let reject = reason => {
    if (this.state === 'pending') {
      this.state = 'rejected';
      this.reason = reason;
      this.onRejectedCallbacks.forEach(fn => fn());
    }
  };
  try {
    executor(resolve, reject);
  } catch (err) {
    reject(err);
  }
}

myPromise.prototype.then = function (onFulfilled, onRejected) {
  // 声明返回的promise2
  let promise2 = new Promise((resolve, reject) => {
    if (this.state === 'fulfilled') {
      onFulfilled(this.value)
    };
    if (this.state === 'rejected') {
      onRejected(this.reason)
    };
    if (this.state === 'pending') {
      this.onResolvedCallbacks.push(() => {
        onFulfilled(this.value)
      })
      this.onRejectedCallbacks.push(() => {
        onRejected(this.reason)
      })
    }
  });
  // 返回promise，完成链式
  return promise2;
}

new myPromise((resolve, reject) => {
  console.log('1')
  resolve(1)
  console.log('2')
}).then((res) => {
  console.log(res)
  console.log('4')
  return 2
})
```

## Promise.all
```javascript
const myPromiseAll = function (promiseList){
    const result = []
    return new Promise((resolve, reject) => {
        let index = 0
        next()
        function next(){
            promiseList[index].then((res) => {
                result.push(res)
                index++
                if(index === promiseList.length){
                    resolve(result)
                } else {
                    next()
                }
            })
        }
    })
    
}
```


# 83. post的方法
- application/x-www-form-urlencoded （url传参数）
- multipart/form-data （上传文件）
- application/json （传json）
- text/xml


# 84. http options预检请求
正式跨域之前，会发起option请求，预检一下。检测发送的请求是否安全，同时发送请求地址，请求方法，服务器判断来源域名是否再许可名单内，请求方法支不支持，支持则允许请求

复杂请求才会发送预检，以下为复杂请求
- put/delete/patch/post的其中一种
- 发送json格式（content-type: application/json）
- 请求中有自定义头部

**为什么要进行预检？**
复杂请求可能会对服务器产生副作用，数据修改等。所以要检测一下请求来源在不在许可名单上

# 85. oop三大特点
- 封装
- 继承
- 多态

# 86. 手写限制并发数
```javascript
function limitPromise(taskList, limit) {
  return new Promise((resolve, reject) => {
    let index = 0
    let active = 0
    let finish = 0
    let result = []

    function next() {
      if (finish >= taskList.length) {
        resolve(result)
        return
      }

      while (active < limit && index < taskList.length) {
        active++
        let cur = index
        taskList[index].then((res) => {
          active--
          finish++
          result[cur] = res
          next()
        })
        index++
      }
    }
    next()
  })
}
```


# 87. webpack的tree shaking
tree shaking是用于清除无用代码的方式，webpack3/4开始之后就自动集成


# 88. getComputedStyle 和 style
- getComputedStyle只读，style可读可写
- style只能获取内联样式

`window.getComputedStyle(dom, null).getPropertyValue('display')`


# 89. 怪异盒模型
- 标准盒模型：宽度 = width + margin + padding + border

假设现在两个div一行放置，都是50%宽，假如我们再期中一个加上边框，这样另一个就会被挤压

这时候我们可以将box-sizing设置为`border-box

- content-box: 默认，标准盒模型
- border-box：border和padding算入width中
- padding-box：padding算入width`

# 90. Object.defineProperty
```
Object.defineProperty(obj, prop, descriptor)

MDN描述：
obj要在其上定义属性的对象。
prop要定义或修改的属性的名称。
descriptor将被定义或修改的属性描述符。
```
- value：设定值
- writable：是否可被重写
- enumberable：是否可枚举（for..in, Object.keys）
- set/get
- configrable：是否可重定义

# 91. HTTP如何复用连接
设置http的header：`Connection: keep-alive`，告诉服务器，待会我还要请求，就可以避免再次三次握手了


# 92. HTTP和TCP的关系
- http是应用层，tcp是传输层
- http是基于tcp的基础上实现的
- tcp只是单纯的进行连接，http是会进行收发数据

# 93. node的优势
- 完全是js语法
- 高并发能力很好
- 非阻塞I/O
- 开发周期短
- 单进程、单线程


# 94. HTTP报文结构
- 请求报文：请求行，请求头，空行，请求数据
- 响应报文，状态行，消息头，空行，响应正文

## 请求头
- 请求方法：get/post
- host：请求主机
- connection：连接状态
- cache-control：缓存
- accept：能发送的类型
- user-agent：代理
- reference：请求资源的url
- accept-encoding：支持的编码方式
- cookie：cookie

## 响应头
- date：响应时间
- last-modify：最后修改时间
- etag：资源标识
- connection：连接状态
- content-type：资源类型



# 95. async / await
## async
async总是返回promise
- 没有显示return，则返回promise.resolve(undefined)
- 返回不是promise的话，则返回promise.resolve(data)
- 返回promise就会得到promise

## await
- await只可以用在async里面
- 如果await后是非promise，则获取里面resolve的值

## 与generator的区别
async就是generator的语法糖

async对比generator的改进
1. 内置执行器，不需要next来执行
2. 更好的语义化
3. 返回promise，可以继续操作

# 96. 是否每一次请求都会三次握手
如果没有缓存的情况下，请求头设置`connection:keep-alive`则可以不重新握手


# 97. TCP的keepAlive和HTTP的keep-alive
- TCP的keepAlive是侧重于保持客户端和服务端的连接，会不定时发送心跳包验证有没有断开连接，如果没有这个机制的话，一方断开，另一方不知道，就会对服务器资源产生较大的影响

- HTTP的keep-alive可以让服务器客户端保持这个连接，不需要重新tcp进行连接了

# 98. TCP两次握手可不可以呢
假如第一次发出连接请求，如果服务器端没有确认，客户端再进行一次请求，然后他们开始连接，在这之后，如果第一次只是延迟了，然后现在发送给客户端，如果没有三次握手的话，就直接开启连接，然而客户端并没有数据要传输，则服务端会一直等待客户端发数据


# 99. TCP三次握手中可以传输数据吗
第一次第二次不可以，因为很容易被人攻击，而第三次握手已经进入establish状态了，已经确认双方的收发能力，可以传输


# 100. 2MSL等待状态
MSL是报文最大生存时间，客户端进入timewait的状态之后，需要等待2msl的时间，这样可以让最后发送的ack不会丢失，保证连接正常关闭，time_wait就是为了防止最后ack重发可能丢失的情况


# 101. websocket
http连接具有被动型，只能主动去向服务器请求看有没有新消息，一直轮询。

websocket是一个持久化的协议，连接了就不会自动断开。而且传递信息的时候只需要传递一点点头信息即可。一次握手，持久连接


# 102. hasOwnProperty
这个方法只会遍历自身属性，不会从原型链上遍历，可以用来判断属性是否在对象上或者是原型链继承来的
```
const obj = new Object()
obj.num = 1

Object.prototype.fn = function(){
    console.log(2)
}

obj.hasOwnProperty(num) // true
obj.hasOwnProperty(fn)  // false
```
