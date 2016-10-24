# 05 - CSS 学习大纲

# 前言

没有CSS的网页，就像没有灵魂的僵尸，丑的不要不要的。

# 基本概念

**层叠式样式表**

- 美化网页：CSS能够对网页进行细致的设计，使其更美观。
- 管理网页：修改样式，能影响所有使用该class的标签显示效果。

**主流版本**

目前主流版本是CSS2 和 CSS3。

CSS2：过去十余年，我们使用的全部都是CSS2，主流浏览器均能良好支持（不同厂家的兼容性问题依然存在）

CSS3：在CSS2的基础上提供了更多的特性，但是IE6,7,8的浏览器不支持（现在已经可以抛弃他们了），其他浏览器支持大部分语法，移动端各种浏览器比较完美支持。

**注意**

我们经常说HTML5的开发，实际上是指 HTML5 + CSS3 + JavaScript(ES5+) 的知识架构，单纯的HTML5并没有什么太大的优势。

# 学习准备

## 资料

- http://www.w3school.com.cn/
- http://www.runoob.com/

## 编辑器

任何一款编辑器均可，editplus、netbeans、HBuilder等。

## 如何运行

CSS不能独立运行，比如加载到HTML文档中。

**和HTML文件混写**

```
<head>
	<meta charset="utf-8" />
	<style>
		body{font-size:12px;}
	</style>
</head>
```

style 标签内所有内容，均为 CSS 代码。

**独立文件**

将CSS 代码独立编写在 .css 文件中。

再通过 HTML link 标签引用。

```
<link href='xxx.css' rel='stylesheet' type='text/css'>
```

# 如何学习

CSS 和 HTML一样，也有两个主要概念，选择器、样式。

## 选择器

你想处理哪个 HTML 标签，就得先选中它！

**语法**

```
#idname{匹配HTML标签 id属性=idname的}
.classname{匹配HTML标签 class属性=classname的}
div{..影响所有div标签}
...
```
- "#"（井号）选择器，选中 html 标签中，id 属性所对应的值
- "."（点号）选择器，选中 html 标签中，class 属性对应的值
- "标签名"选择器，选中html中，指定的标签，比如 div、p ...
- 还有多层选择器，请大家自行手册查阅

## 样式

选中了目标元素之后，对它具体做什么呢？

**语法**

- 样式语法必须写在选择器的{}里面
- 每个样式用 样式名：值 的格式。
- 多个样式之间用；号间隔开

```
/*设置目标元素文字大小 = 12像素，颜色 = red红色*/
.classname{font-size:12px; color:red;}
```

**有哪些样式可用**

还是看资料吧 [http://www.w3school.com.cn/cssref/index.asp](http://www.w3school.com.cn/cssref/index.asp) 

抽点时间，把里边所有的属性都大致看一遍，你也就入门了。

# 结语

CSS 入门不是很难，对基础的选择器和样式语法有了解即可，但是深入CSS 比较痛苦。

因为大多数教程都是浮于表面的，什么实现XXX效果。正牌的文档大多数是英文，说的又比较晦涩，加上各种不同的客户端环境（不同的浏览器，移动端等）。

所以特别专业的前端设计，交给设计师去做吧。如果你们公司只有一个搞技术的，算我没说。

> 你可以做不出好看的页面，但必须懂CSS的语法。