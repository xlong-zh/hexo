---
title: DOM
tags: html
categories: html
---

# HTML5

● 新的语义元素，比如 <header>, <footer>, <article>, and <section>。
● 新的表单控件，比如数字、日期、时间、日历和滑块。
● 强大的图像支持（借由 <canvas> 和 <svg>）
● 强大的多媒体支持（借由 <video> 和 <audio>）
● 强大的新 API，比如用本地存储取代 cookie。
● WebSocket

# 块元素

div、p、nav、aside、header、footer、section、article、ul-li、address 等

1. 独霸一行，总是在新行上开始
2. 宽度缺省是它父级元素的 100%，除非设定一个宽度
3. 高度、行高、外边距、内边距都可以设置
   可以容纳其他内联元素或者其他块元素

# 行内元素

行内元素最常使用的就是 span，其他的只在特定功能下使用，修饰字体<b>和<i>标签，还有<sub>和<sup>这两个标签可以直接做出平方的效果，而不需要类似移动属性的帮助，很实用。
行内元素特征：
(1)设置宽高无效
(2)对 margin 仅设置左右方向有效，上下无效；padding 设置上下左右都有效，即会撑大空间
(3)不会自动进行换行

# api

nodeType 辨别类型
childNodes 会包含文档和空子节点
Children 只找元素子节点（非标属性，但都支持）
parentNode 父节点
parentElement 父元素节点（IE9 以下不兼容）
nextElementSibling 下个兄弟节点
previousElementSibling 上个兄弟节点
firstElementChild 第一个子节点
lastElementChild 最后一个子节点

//创建元素
document.createElement('标签的名字');
//插入元素：（向父级末尾添加一个元素）
parentNode.appendChild(childNode)
//插入元素：（向父级中的某个元素前插入元素）
parentNode.insertBefore(新添加的元素,已有的元素)
//删除节点:
父级.removeChild(指定的子节点)
//替换节点:
父级.replaceChild(要替换成什么,谁被替换)    
//克隆节点:
元素.cloneNode()
(有参数，默认为 false)，true 可以克隆该元素下的所有子节点；
事件是不会被克隆的！！！

//获取元素行间的属性
elem.getAttribute('key')
//设置元素的行间属性
elem.setAttribute('key','value')  
//删除元素的行间属性
elem.removeAttribute('key')
Eg: <div index='1'></div>

//最近的有定位属性的祖先节点，默认为 body
offsetParent
//左外边框到有定位父级的左内边框的距离
offsetLeft
//上外边框到有定位父级的上内边框的距离
offsetTop
//获取元素的宽高（加 padding，不计算边框）
elem.clientWidth/ elem.clientHeight     
//获取元素的宽高（加 padding，计算边框）    
elem.offsetWidth/ elem.offsetHeight
//可视区的宽高：
document.documentElement.clientWidth/
document.documentElement.clientHeight
