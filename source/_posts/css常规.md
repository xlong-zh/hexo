---
title: css常规
tags: css
categories: css
---

&nbsp 识别为一个空格 &lt &gt 大小于符号 %copy @

# 文本溢出

## 多行文本溢出：

word-break: break-all;
text-overflow: ellipsis;
display: -webkit-box; /** 对象作为伸缩盒子模型显示 **/
-webkit-box-orient: vertical; /** 设置或检索伸缩盒对象的子元素的排列方式 **/
-webkit-line-clamp: 2; /** 显示的行数 **/
overflow: hidden; /** 隐藏超出的内容 **/

## 单行文本溢出：

overflow: hidden;
text-overflow:ellipsis;
white-space: nowrap;

# 一些实现功能的语法

1. 针对节点新增 class 并且不覆盖原有 clas
   item.classList.add("");
2. 针对节点删除固定 class 并且不影响原有 clas
   item.classList.remove("");
3. 判断一个节点是否有某个 class 属性
   item.classList.contains("red")
   classList.toggle 是有这个类就删除 没有就添加

# background 简写顺序

background-color background-image background-repeat background-attachment background-position

# rem 适配方案

window.onload = function () {
            /_720 代表设计师给的设计稿的宽度，你的设计稿是多少，就写多少;100 代表换算比例，这里写 100 是
               为了以后好算,比如，你测量的一个宽度是 100px,就可以写为 1rem,以及 1px=0.01rem 等等_/
            getRem(720, 100)
        };
        window.onresize = function () {
            getRem(720, 100)
        };
        function getRem(pwidth, prem) {
            var html = document.getElementsByTagName("html")[0];
            var oWidth = document.body.clientWidth || document.documentElement.clientWidth;
            html.style.fontSize = oWidth / pwidth \* prem + "px";
        }

# 1 像素边框

![](/images/yxsbk.jpg)

# 裁剪属性

图片裁剪为菱形
mg {
clip-path: polygon(50% 0%, 100% 50%, 50% 100%, 0% 50%);
}

# 清除浮动

.clearfix:after{/_伪元素是行内元素 正常浏览器清除浮动方法_/
content: "";  
 display: block;
height: 0;
clear:both;
visibility: hidden;
}
.clearfix{
*zoom: 1;/*ie6 清除浮动的方式 _号只有 IE6-IE7 执行，其他浏览器不执行_/
}

# 浏览器响应式布局

1、em 具有继承性 浏览器文字默认 16px 1em=16px
2@media 属性「媒体查询」，称为响应式布局 1)语法 @media screen and（max-width：1000px；）
2）如果尺寸样式样式很多，需要不同的 css 去外联，此时需要在引用的时候添加判断条件，以免浏览器以此读取 css 样式，语法：<link rel="stylesheet" href="./max1000.css" media="sceren and (max-width:1000px)">

# 字体

1、font-size:定义字符框高度（不要写奇数）可以继承 有预设值 尽量大于 12 不要有小数点
2、font-weight:加粗字体 可以定义属性值为 bold ，也可以为数值
3、font-style：控制文字倾斜 normal 为不倾斜 italic 为倾斜
4、letter-spacing:10px; 文字的间隙为 10 个像素 字符和字符之间
5、word-spacing：xx px；词间距 通过空格键去识别
5、text-indent:xx px;首行缩进 em px
6、font-family：“宋体”，“黑体”；（谨慎使用 版权问题）

# 边框

1、border-radius 设置圆形边框
2、background-img 背景图片
3、background-repeat 设置图片重复方式 实现自适应？ 见第五条
4、background-position 可以取 xy 的值 也可以取 left right bottom middle
5、background-size：（contain）/（cover）。数字 数字。 100% auto
6、background-attachment：fixed；背景图片固定化不动
7、bgc 的简写顺序：颜色 路径 平铺方式 位置
8、background：linear-gradient（颜色 1 颜色 2）/（to right 颜色 1 颜色 2）实现渐变效果
9、background-color{ 声明颜色后尾部加一个数字 是透明度 0.5 代表 50%}透明度
10、box-shadow：5px 10px 10px 颜色。 盒子阴影 模糊程度 外延【x-y】 颜色 阴影不占像素
11、text-shadow：与 boxshadow 写法一样 没有外延
12、display：none； visibility:hidden;
