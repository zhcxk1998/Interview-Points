# Interview-Points
这是一个用来存放面试知识点的整理记录

[toc]


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
}
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

非简单请求会在正式通信之前，增加一次HTTP查询请求，成为预检请求

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

# 30. 

