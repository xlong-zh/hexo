---
title: js基础
tags: js
categories: js
---

# 数据类型转换

显式类型转换（强制类型转换）：
Number()
parseInt()
parseFloat()

隐式类型转换：
    +        200 + '3'        变成字符串
    - \* / %     '200' - 3 变成数字
    ++ --          变成数字
    > <           数字的比较 、字符串的比较
    !    取反       把右边的数据类型转成布尔值
    ==

# 浏览器缓存

1. localStorage 本地，没有时间限制，关闭浏览器也存在。除非主动删除，否则一直存在
2. sessinStorage 阶段，临时保存，当窗口关闭就被删除
   都是以键值对的形式保存
   // --------------- 方法
   // 1. 添加 localStorage.setItem("key", "value");
   // localStorage.setItem("username", "zhangsan");
   // 2. 获取 localStorage.getItem("key");
   // localStorage.getItem("username");
   // 3. 删除 localStorage.removeItem("key");
   // localStorage.removeItem("username");
   // 4. 清空 localStorage.clear();
   // localStorage.clear();
   let store = {
   set(key, value) {
   localStorage.setItem("key", JSON.stringify(value));
   },
   get(key) {
   return JSON.parse(localStorage.getItem("key")) || [];
   }
   }
