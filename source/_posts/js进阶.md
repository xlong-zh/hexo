---
title: js进阶
tags: js
categories: js
---

# 事件循环机制

JS 是单线程语言，JS 任务分为同步任务和异步任务，同步任务都在主线程上执行，形成一个执行栈，在执行栈中一个任务执行完后才会执行下一个任务。如果遇到异步任务则将异步任务挂起，先执行后面的同步任务，异步任务有了运行结果后会将异步回调放入任务队列中，一旦"执行栈"中的所有同步任务执行完毕，系统就会读取"任务队列"，如果存在将任务队列中的任务放入主线程中执行。异步任务中又有宏任务和微任务[Promise],微任务会先于宏任务执行。
![](/images/hrw.jpg)

# 闭包

## 闭包的概念

闭包就是函数和函数上下文环境的捆绑组合，当函数执行完后，函数中的变量就会被销毁，但是闭包在返回函数的同时将这个函数的上下文环境存储在内存中，可以让内层函数访问到外层函数的变量。

## 闭包的应用

### 函数柯里化

```
/**
柯里化的作用 => 1.参数复用 2.解耦
现在需要一个函数fn(reg,rule)传入两个参数，第一个是匹配规则，第二个是要检查的值，
检查传入的值是否符合传入的规则，返回检查结果
*/
//普通函数形式
function regMatch(text,rule){
    const reg = new RegExp(rule)
    if(reg.test(text)) return true
    return false
}
const isPhone = regMatch('13308041085',/^1\d{10}$/)

//柯里化形式
function regMatch(rule){
    return function(text){
         const reg = new RegExp(rule)
         if(reg.test(text)) return true
         return false
    }
}
const isPhone = regMatch(/^1\d{10}$/);
const isPhontRsult = isPhone('13308041085');
```

### 高阶函数

```
/**
函数作为参数传或者函数作为返回值被返回的函数叫做高阶函数,可以理解为高阶函数就是函数的加工工厂
*/
//节流（监听鼠标移动时间，鼠标1s内移动1万次，控制只执行10次，100ms执行一次）
function throttle(fn, delay) {
  let timer = null;
  const _this = this;
  return function (...args) {
    if (!timer) {
      timer = setTimeout(() => {
        fn.apply(_this, args);
        clearTimeout(timer);
        timer = null;
      }, delay);
    }
  };
}
//防抖（一个按钮，不断的点击，1s内点击100次，控制只执行最后一次的点击事件）
function debounce(fn, delay) {
  let timer = null;
  const _this = this;
  return function (...args) {
    if (timer !== null) clearTimeout(timer);
    timer = setTimeout(()=>{
      fn.apply(_this,args)
    }, delay);
  };
}

```

# 修改 this 指向

obj.myFun.call(db,'成都','上海')；　　 // 德玛 年龄 99 来自 成都去往上海
obj.myFun.apply(db,['成都','上海']); // 德玛 年龄 99 来自 成都去往上海  
obj.myFun.bind(db,'成都','上海')(); // 德玛 年龄 99 来自 成都去往上海

# 原型链

构造函数构造出的实例对象上有**proto**属性，指向构造函数的 prototype，prototype 上是构造函数的公共属性，当访问对象的属性，并且对象上不存在这个属性时就会通过**proto**向上查找构造函数的 prototype 上是否存在这个属性，原型链的作用就是为了实例对象能继承构造函数上的公共属性。

```
const a = {name:2}
a.__proto__ === Object.prototype // => true      实例对象的_proto_ 指向其构造函数的prototype
/**
a这个对象本身没有toString这个属性 但是他的构造函数Object上有toString属性
*/
a.toString()
```

## 继承

### new 关键字

```
function _New(fun) {
        //首先会创建一个新的空对象
        var obj = {};
        //然后新的空对象的_proto_指向构造函数的prototype成员对象
        obj._proto_ = fun.prototype;
        //创建一个引用对象,并且把构造函数（fun）的this指向引用对象
        var res = fun.call(obj);
        //判断构造函数执行完的结果返回的是不是一个对象，如果是就返回这个对象；如果不是，就返回新创建的对象（obj）
        if (res && typeof (res) == 'object' || typeof (res) == 'function') {
            return res;
        } else {
            return obj;
        }
    }
```

### 原型链继承

```
/**
通过原型链继承  实例可以继承[继承对象]的属性和prototype属性
*/
function Parent(name){
	this.type = 'parent';
  this.name = name;
}
function Child(name){
	this.fill = 'fade';
  this.name = name;
}
Parent.prototype.post = function(){ console.log('post to child') }
Child.prototype = new Parent();
Child.prototype.constructor = Child
Child.prototype.get = function(){ console.log('receive from parent') }
let parent = new Parent('A')
let child = new Child('B')
```

### class 继承

```
class person {
 constructor(){
 this.kind="person"
 }
 eat(food){
 console.log(this.name+" "+food);
 }
}

class student extends person{
 constructor(name){
 super();
 this.name=name;
 }
}
var martin=new student("martin");
console.log(martin.kind); //person
martin.eat("apple"); //martin apple
```
