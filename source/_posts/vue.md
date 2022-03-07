---
title: vue
tags: vue
categories: vue
---

# 生命周期

Vue 的生命周期就是 Vue 实例从创建到销毁的过程，通过构造函数生成 Vue 实例后，会初始化生命周期和事件，然后触发 beforecreate 钩子函数，接下来 vue 会把通过 Object.defineProperty()将 data 中的数据变成可观测数据，然后触发 created 钩子，此时会将 template 模板编译成 render 函数，然后会触发 beforeMount 钩子函数，之后会将虚拟 dom 生成真实 dom 节点并切挂在 el(容器)上，之后会触发 mounted 钩子函数，在 mounted 钩子中，已经可以拿到并操作真实 dom 节点，当 data 中的数据更新时会触发 beforeUpdate 钩子，新旧 virtualDom 对比后通过 patch 函数重新渲染更新的节点。vue 实例销毁前会触发 beforeDestroy 钩子，销毁后触发 destroyed 钩子，一般在销毁的时候会清除计时器和一些监听事件。

# 响应式原理

Vue 在 created 生命周期前会遍历 data 中的属性，通过 Object.defineProperty()给 data 中的每个数据都添加 get 和 set 属性，当数据被使用时就会触发 get 方法，通知 watcher 记录依赖关系，当数据被修改时会触发 set 方法，wacher 会通知依赖的订阅者修改视图更新数据。

# diff 算法

vue 在对比虚拟 dom 时会采用同层级对比的策略，同层级的 dom 只会和同层级的 vdom 进行比较，并且只有新旧 vdom 的 key 相同并且选择器相同时，才会进行后续对比，否则直接替换掉节点，不会进行后续对比。
