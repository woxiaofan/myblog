---
layout: photo  
title: particles.js创造页面整体背景效果图  
date: 2017-03-03 12:14:39  
tags: "web前端"  
categories: "Hexo博客"  
photos:  
- http://www.ityyf.me/image/particles01.jpg  
- http://www.ityyf.me/image/particles02.jpg
- http://www.ityyf.me/image/particles03.jpg   
---
___

<blockquote class="blockquote-center">如上相册所示，背景效果图分别是经典版、泡泡版和下雪版  
                                      以下介绍经典粒子版本的Hexo博客嵌入方法  
                                      最终效果如此篇博客背景动态（跟随鼠标变换）</blockquote><!--more-->
___

# 准备工作

<br>

> 说明：这个背景图并不是一个单纯的Gif图，而是用Js根据鼠标的移动而计算出来的一个canvas画布技术

为了简单方便考虑，这里暂且不介绍Js的代码含义，仅仅贴出文件供大家参考和使用。这个需要用到如下两个JS文件  
__[particles.js](http://www.ityyf.me/js/src/particles.js)__ 和配置文件 __[app.js](http://www.ityyf.me/js/src/app.js)__  
一个CSS文件  
__[style.css](http://www.ityyf.me/css/style.css)__  

# 文件部署 
 
<br>

有了这几个核心文件之后，需要了解一下Hexo页面的生成内部机制原理  
![loading...](../../../../../image/hexo_next.png)  
如上图所示，hexo的主页面index.html自动生成的源文件为_layout.swig，因此可以理解为主页面的源文件为这个，任何操作在里面修改即可（可根据自己博客的主题来进入响应的原文件夹中寻找文件）  
![loading...](../../../../../image/hexo_next0.png)  
如上图所示：将以上两个JS文件和一个CSS文件分别放入红色框内的对应位置（严格来说只要是source目录下的任何位置都是ok的，只要你路径引入正确即可）  

# 页面写入

<br>

打开刚才的首页原文件_layout.swig，引入两个JS文件和一个CSS源码  
```
<link rel="stylesheet" type="text/css" href="css/style.css">
<script src="js/src/particles.js"></script>
<script src="js/src/app.js"></script>
```

另外由于这个是通过画布技术写的特效，因此页面上需要一块位置来存放画布画出来的内容
```
<div id="particles-js"></div>
```

__上述一行代码很重要！页面上必须要有这一个div！__  

至此，已经部署完毕，`hexo g` + `hexo s`后打开`http://localhost:4000`预览效果吧

# 效果完善

<br>

> 通过上述步骤之后你会发现index.html能够看得到效果了，但是还是存在一些很严重的问题，常见问题如下

## 位置显示有误

位置情况大致分两种，一种是在页面最上边，一种是在页面最底端，归根结底是由于博客的主题包里面的三种模式造成的影响，不过可以通过对其进行强制定位:

```css
#particles-js{
  position: fixed;
  top: 0;
	width:100%;
	height:95%;
}
```

## 页面布局混乱

此问题主要是由于style.css的初始化对hexo其他页面造成了冲突所造成的，只需要找到此css文件，将里面的初始化内容注释掉或者直接删除即可

## 页面部分模块被遮挡

由于不同主题层级关系，创建的画布div可能位于你所要点击的div上，因此只需调节下层级关系即可

层级关系有如下方法调节：  

1、将画布创建到主内容下  
```
<div class="{{ container_class }} {% block page_class %}{% endblock %} ">
<div id="particles-js"></div>
```
2、通过最原始的源码z-index调节层级

## 二级甚至三级页面无效

打开控制台，会发现js和css文件找不到，那是因为路径的问题

导航模块需要再退一层，文章需要再退一层

不同情况路径不同，此博客由于最深的路径为文章页，根据情况，需要退5层，因此将路径改为

```text
<link rel="stylesheet" type="text/css" href="../../../../../css/style.css">
<script src="../../../../../js/src/particles.js"></script>
<script src="../../../../../js/src/app.js"></script>
```

<strong>这里未列出来的问题可至留言区留言，有空回复</strong>

另外配置文件app.js中的样式，可移步至官方技术文档详解
[https://github.com/VincentGarreau/particles.js](https://github.com/VincentGarreau/particles.js)
