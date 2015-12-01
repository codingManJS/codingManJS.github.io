---
layout: post
title: 胡说call,apply,bind
category: JavaScript
---
2015-12-01
>  学过一点javascript的都知道call，apply，bind这三个货，能够改变函数的this指向，反正我也很糊涂搞三个干嘛，有什么区别呢？

###  call
首先看看MDN的解释：
>    call()方法在使用一个指定的this值和若干个指定的参数值的前提下调用某个函数或方法.

再看看语法：
>  fun.call(thisArg[, arg1[, arg2[, ...]]])

能看出来call是function的方法，它第一个参数是要指向的对象，后面跟若干参数...

看看例子吧：
```javascript   
function a(){
  this.name = 'metro'
}
//普通执行函数
a()//这时this指向的全局变量假设在浏览器的话window.name为metro
var b = {}
a.call(b)//这时候this指向的就是b对象
console.log(b.name)//'metro'
```
>  Array.prototype.slice.call(arguments)  都看过这个吧...

要想知道这段代码的意义，首先array的slice是干嘛的，看代码吧

```javascript

var a = [1, 2, 3, 4]
a.slice(0,1)//[1]
a.slice(2)//[3, 4]
var b = a.slice()
//b = [1, 2, 3, 4]

```

所以Array.prototype.slice这个东西可以返回一个数组，当然参数很重要，不传参数相当于复制一个数组，其他的很好理解，返回数组从start到end的位置元素.
Array.prototype.slice.call(arguments)
首先它是复制一个数组的代码形式，call呢，就是改变slice中的this指向，arguments不用解释了，所以这个就是把arguments返回成数组的形式。

###  apply

其实apply和call没啥区别，我感觉啥玩意，要说有区别那就是参数个数不一样，apply是两个，第一个也是改变this指向的对象，第二个是数组（其实没啥区别，看看代码）
```javascript
function a(n, m) = {
  this.name = n
  this.age = m
}
var metroArr = ['metro', 22]
var metroObj = {}
a.apply(metroObj, metroArr)
a.call(metroObj, metroArr[0], metroArr[1])
//对比一下代码，真心没啥区别，
//那apply就这样了，和call差不多
```

### bind

其实感觉bind和前面call也差不多。。但是得注意一点就是bind返回函数，bind传参数的形式和call一样的，一摸一样的，就不讲了吧

看看代码如何？
```javascript
function a(){
  console.log(this.name)
}
var metro = {
  name: 'metro'
}
var b = a.bind(metro)
b()//打印metro
看着代码琢磨一下和call也没啥区别，但是三个函数重点是改变this指向，这个需要好好理解一下
```
