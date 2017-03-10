---
title: CSS Hack技术  
date: 2017-03-10 17:23:14  
categories: CSS  
tags: web前端
---

<blockquote class="blockquote-center">Hacker:黑客<br>CSS Hack:据此而来，通过浏览器解析漏洞从而衍生的兼容性调节技术</blockquote>

![hacker...](../../../../../image/hacker.jpg)

<!--more-->

# Hack概念

不同的浏览器对CSS的解析结果是不同的，因此会导致相同的CSS输出的页面效果不同，这就需要CSS Hack来解决浏览器局部的兼容性问题。而这个针对不同的浏览器写不同的CSS 代码的过程，就叫CSS Hack。

## CSS属性Hack

IE6能识别下划线`_`和星号`*`，IE7能识别星号`*`，但不能识别下划线`_`，而firefox两个都不能认识

## CSS选择符Hack

__IE6__ 能识别`*html .className{}`，IE7能识别`*+html .className{}`或者`*:first-child+html .className{}`。

## IE条件注释Hack

IE条件注释是微软从 __IE5__ 开始就提供的一种非标准逻辑语句。比如针对所有IE：`<!–[if IE]><!–您的代码–><![endif]–>`，针对 __IE6__ 及以下版本：`<!–[if lt IE 7]><!–您的代码–><![endif]–>`，这类Hack不仅对CSS生效，对写在判断语句里面的所有代码都 会生效。

> 条件注释只有在IE浏览器下才能执行，这个代码在非IE浏览下被当做注释视而不见。可以通过IE条件注释载入不同的CSS、JS、HTML和服务器代码等。

___

# 常用的CSS Hack

## CSS属性Hack

- `color:red;` __IE*__
- `_color:red;` __IE6__
- `*color:red;` __IE6__ + __IE7__
- `+color:red;` __IE6__ + __IE7__
- `*+color:red;` __IE6__ + __IE7__
- `color:red\9;` __IE6__ + __IE7__ + __IE8__ + __IE9__
- `color:red\0;` __IE8__ + __IE9__
- `color:red\9\0;` __IE9__
- `color:red!important;` __!IE6__

## CSS选择符Hack

- `*html #demo { color:red;}` __IE6__
- `*+html #demo { color:red;}` __IE7__
- `body:nth-of-type(1) #demo { color:red;}` __IE9+、FF3.5+、Chrome、Safari、Opera__
- `head:first-child+body #demo { color:red; }` __IE7+、FF、Chrome、Safari、Opera__
- `:root #demo { color:red\9; }` __IE9__

## IE条件注释Hack

- `<!--[if IE]>此处内容只有IE可见<![endif]-->` 
- `<!--[if IE 6]>此处内容只有IE6.0可见<![endif]-->` 
- `<!--[if IE 7]>此处内容只有IE7.0可见<![endif]-->` 
- `<!--[if !IE 7]>此处内容只有IE7不能识别，其他版本都能识别，当然要在IE5以上。<![endif]-->`
- `<!--[if gt IE 6]> IE6以上版本可识别,IE6无法识别 <![endif]-->`
- `<!--[if gte IE 7]> IE7以及IE7以上版本可识别 <![endif]-->`
- `<!--[if lt IE 7]> 低于IE7的版本才能识别，IE7无法识别。 <![endif]-->`
- `<!--[if lte IE 7]> IE7以及IE7以下版本可识别<![endif]-->`
- `<!--[if !IE]>此处内容只有非IE可见<![endif]-->`

___

以上为常用的CSS Hack用法，详情请移步至 __[CSS Hack技术介绍及常用的Hack技巧集锦](https://zm10.sm-tc.cn/?src=l4uLj8XQ0JLRlZ3KztGRmovQnIyM0M3NycfHx9GXi5KT&uid=d5b5963465aff2c09555ffa146156bd1&hid=1325689c9f9358cdc4693490c8c5c640&pos=1&cid=9&time=1489115262923&from=click&restype=1&pagetype=0080004002000402&bu=news_natural&query=css+hack%E6%8A%80%E5%B7%A7&mode=&v=1&uc_param_str=dnntnwvepffrgibijbprsvdsei)__