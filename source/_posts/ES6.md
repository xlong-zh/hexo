---
title: ES6
tags: js
categories: js
---

# let和const
var是函数作用域，在函数体内声明的不能在函数体外访问；let和const是块作用域，代码块内声明后不能在代码块外访问，let和const不存在变量提升，通过const声明的变量作为常量，在声明后不能再进行赋值操作；
# 解构
```
//解构赋值
let { foo, bar } = { foo: 'aaa', bar: 'bbb' };
foo // "aaa"
bar // "bbb"
let [x, y] = [1, 2, 3];
x // 1
y // 2
//rest参数
let { foo,...rest } = { foo: 'aaa', bar: 'bbb',baz:'baz' };
rest // { bar: 'bbb',baz:'baz' }
```
# 扩展运算符
```
//数组合并
const a = [1,2,3,4];
const b = [2,3,4,5];
const d = [...a,...b]; // =>[1, 2, 3, 4, 2, 3, 4, 5]
//对象合并
const o1 = { name:22,age:33,gender:'male' };
const o2 = { age:23,weight:20 };
const o3 = { ...o1,...o2 }; // =>{name: 22, age: 23, gender: 'male', weight: 20} 后会覆盖前
```
# 模板字符串
```
const a = 'zola'
const b = `this is  ${ a }` // => this is zola
```
## 字符串新增方法
### includes
```
// includes()：返回布尔值，表示是否找到了参数字符串。
'MerryChristmas'.includes('mer') // => true
```
### replaceAll
```
//replaceAll()方法，可以一次性替换所有匹配,返回新的字符串，不会改变原字符串 (字符串的实例方法replace()只能替换第一个匹配)
 'MerryChristmas'.replaceAll('r','x') // =>'MexxyChxistmas'
```
### 正则构造函数
```
 var regex = new RegExp('xyz', 'i');
 // 等价于
 var regex = /xyz/i;
 ```
 # 函数的扩展
 ## 默认参数
 ```
function log(x, y = 'World') {
  		console.log(x, y);
		}
```
## 可变参数
```
function aa(...r){ console.log(r) } // =>  [1, 2, 3, 4] 可以在参数个数不确定的情况下获取传入的所有参数，代替arguments
```
## 箭头函数
```
const a = ()=>{ return 'a' } //箭头函数没有自己的this上下文，指向函数外层
```
## try...catch
```
//JavaScript 语言的try...catch结构，以前明确要求catch命令后面必须跟参数，接受try代码块抛出的错误对象。
try {
  // ...
} catch {
  // ...
}
```
# 数组的扩展
## Array.from
```
//Array.from 将类数组转换成数组
let arrayLike = {
    '0': 'a',
    '1': 'b',
    '2': 'c',
    length: 3
};
let arr2 = Array.from(arrayLike); // ['a', 'b', 'c']
```
## Array.of
```
//Array.of()方法用于将一组值，转换为数组。
Array.of(3, 11, 8) // [3,11,8]
```
## find
```
//数组实例的find方法，返回找到的第一个符合条件的数组成员，没有找到泽返回undefined
[1, 4, -5, -10].find((n) => n < 0) // => -5
```
## includes
```
//Array.prototype.includes方法返回一个布尔值，表示某个数组是否包含给定的值，与字符串的includes方法类似
[1, 2, 3].includes(2)     // true
```
## flat
```
/**
Array.prototype.flat()用于将嵌套的数组“拉平”，变成一维的数组。该方法返回一个新数组，对原数据没有影响。
如果不管有多少层嵌套，都要转成一维数组，可以用Infinity关键字作为参数。
*/
[1, 2, [3, 4]].flat() // =>[1, 2, 3, 4] 
[1, [2, [3]]].flat(Infinity) //=>[1, 2, 3]
```
## sort
```
//Array.prototype.sort() 的排序稳定性
let nums = [2,3,12,33,4,234,16,22,68,12]
let data = nums.sort((a,b)=>{
    console.log({a,b})
    return a - b // 从小到大 b-a 从大到小
})
```
# 对象新增方法
## Object.keys()
```
//遍历对象的key
var obj = { foo: 'bar', baz: 42 };
Object.keys(obj)
// ["foo", "baz"]
```
## Object.assign()
```
//合并对象，返回合并后的对象
const target = { a: 1 };
const source1 = { b: 2 };
const source2 = { c: 3 };
Object.assign(target, source1, source2);
target // {a:1, b:2, c:3}
```
## Set和Map数据
### Set
```
//ES6 提供了新的数据结构 Set。它类似于数组，但是成员的值都是唯一的，没有重复的值。
const d = Array.from(new Set([2,3,12,33,4,234,16,22,68,12]) //Set是类数组)
```
### Map
```
/**
Map类似于对象，也是键值对的集合，但是“键”的范围不限于字符串，各种类型的值（包括对象）都可以当作键
*/
const m = new Map();
const o = {p: 'Hello World'};
m.set(o, 'content')
m.get(o) // "content"
m.has(o) // true
m.delete(o) // true
m.has(o) // false
```
# Class
```
//class替代构造函数
class Point {
  constructor(x, y) {
    this.x = x;
    this.y = y;
  }

  toString() {
    return '(' + this.x + ', ' + this.y + ')';
  }
}
//class的继承 (extends关键字)
class ColorPoint extends Point {
}
```
# Promise
```
const promise = new Promise(function(resolve, reject) {
  // ... some code

  if (/* 异步操作成功 */){
    resolve(value);
  } else {
    reject(error);
  }
});
```
# async
```
async function getStockPriceByName(name) {
  const symbol = await getStockSymbol(name);
  const stockPrice = await getStockPrice(symbol);
  return stockPrice;
}

getStockPriceByName('goog').then(function (result) {
  console.log(result);
});
```
# module
```
//export和import
export const firstName = 'Michael';
export const lastName = 'Jackson';
export const year = 1958;
import { firstName, lastName, year } from './profile.js';

export default { firstName, lastName, year }
import params from './profile.js';



//动态加载
import()函数可以用在任何地方，不仅仅是模块，非模块的脚本也可以使用。它是运行时执行，也就是说，
什么时候运行到这一句，就会加载指定的模块。
```