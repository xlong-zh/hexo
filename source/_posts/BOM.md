---
title: BOM
tags: html
categories: html
---

# BOM

## 浏览器渲染机制

### 渲染机制

先解析 html 生成 dom 树，再解析 css 生成 css 树，将 dom 和 css 树结合生成 render 树，开始回流解析 render 树，获取每个节点的尺寸和位置信息，根据获取的信息开始重绘将页面渲染到浏览器中；

### 重绘和回流

#### 重绘

DOM 节点的样式信息(颜色背景等)发生改变时，浏览器会重新渲染 dom 节点，这个过程叫做重绘；

#### 回流

DOM 节点的位置信息和尺寸信息发生改变时，浏览器会通过重新计算 render 树获取节点的尺寸和位置信息，这个过程就叫回流；

#### 重绘和回流的关系和优化

回流一定会发生重绘，重绘不一定会导致回流。回流的开销要大于重绘，所以要尽可能避免多次发生回流，避免操作 dom 时频繁的改变元素的尺寸和位置信息，可以通过修改 class 的形式，一次性修改完毕，在动态生成 dom 节点的时候，也可以拼接好 html 后再做 dom 替换。使用 resize、scroll 时进行防抖和节流处理，这两者会直接导致回流。

# bgc

![](/images/bfc.jpg)

# 事件绑定多个函数（兼容）：

function bind(obj, evname(事件名称), fn(事件函数)) {
    if (obj.addEventListener) {
        obj.addEventListener(evname, fn, false(是否捕获));
    } else {
        obj.attachEvent('on' + evname, function() {
            fn.call(obj);
        });
    }
}
//是否捕获 : 默认是 false； false:冒泡 true：捕获

## 事件绑定形式的取消

Btn.onclick=null //普通绑定
ie : obj.detachEvent(事件名称，事件函数);
标准 : obj.removeEventListener(事件名称，事件函数，是否捕获);

备注：
ie：obj.attachEvent(事件名称，事件函数);
    1.没有捕获
    2.事件名称有 on
    3.事件函数执行的顺序：标准 ie-》正序 非标准 ie-》倒序
    4.this 指向 window
标准：obj.addEventListener(事件名称，事件函数，是否捕获);
    1.有捕获
    2.事件名称没有 on
    3.事件执行的顺序是正序
    4.this 触发该事件的对象

# api

window.navigator.userAgent --> 浏览器信息
window.location -->浏览器地址信息
window.location.href:url
window.location.search:url -->?后面的内容
window.location.hash:url -->#后面的内容

# 事件

obj.focus() 给指定的元素设置焦点
obj.blur() 取消指定元素的焦点
obj.select() 选择指定元素里面的文本内容
Onfocus 当元素获取到焦点的时候触发
onblur 当元素失去焦点的时候触发
oncontextmenu 右键菜单事件，当环境菜单显示出来时触发
onscroll 当滚动条滚动的时候触发
Onresize 当窗口大小发生改变的时候出发
onkeydown 当键盘按键按下的时候触发
onkeyup 当键盘按键抬起的时候触发
event.keyCode 数字类型 键盘按键的值 键值
ctrlKey,shiftKey,altKey 布尔值，当一个事件发生的时候，如果 ctrl/shift/alt 是按下的状态，返回 true，否则返回 false

# 当一个事件发生的时候，鼠标到页面可视区的距离

clientX[X] clientX[Y]

## 事件冒泡

当一个元素接收到事件的时候，会把他接收到的所有传播给他的父级，一直到顶层 window.事件冒泡机制

## 阻止冒泡: 当前要阻止冒泡的事件函数中调用

event.stopPropagation() //停止冒泡
event.cancelBubble = true; ie 低版本

## 事件默认行为：当一个事件发生的时候浏览器自己会默认做的事情；

阻止默认行为：return false;
return false 阻止的是 obj.on 事件名称=fn 所触发的默认行为；
addEventListener 绑定的事件需要通过 event 下面的 preventDefault();
ie 低版本阻止事件默认行为：event.returnvalue=false
eg:
if (ev.preventDefault) {
            ev.preventDefault();
        }
return false;

## 小计

1、event.stopPropagation() //停止冒泡
2、IE 低版本事件对象 window.event 停止冒泡 event.cancelBubble=true;
3、阻止 a 标签跳转 //阻止事件默认行为 event.preventDefault();
4、ie 低版本阻止事件默认行为 event.returnvalue=false

# 事件委托

将事件绑定在祖先元素身上的方式被称为事件委托
//原理 利用冒泡的机制，只指定一个事件处理函数就可以管理一类事件，把具体子节点上发生的事情交给更大范围去处理
//什么时候使用：子级数量很多的时候 子级动态生成的时候
//写法：event.target.nodeName==?
event.target.id==?
event.target.className==?

# 鼠标滚动事件的区别

ie/chrome : onmousewheel
        event.wheelDelta
             上：120
             下：-120
firefox : DOMMouseScroll 必须用 addEventListener
        event.detail
             上：-3
             下：3
