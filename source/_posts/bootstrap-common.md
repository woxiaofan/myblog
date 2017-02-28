---
title: BootStrap框架常用语法  
date: 2017-01-08 21:09:54  
tags: web前端  
categories: bootstrap 
---
# 文档结构
- 需要使用HTML5文档结构 `<!DocType html>`
- 移动设备优先    需要在头部增加`<meta>`标签
  
```html
<meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1,initial-scale=1.0"/>
```
- 引入BootStrap
    - 引入css，当有自己的css文档，应引入bootstrap.css后再引入自己编写额css文件
    - 引入jQuery.js再引入bootstrap.js
    - 若要兼容IE浏览器，再引入两个js文件，使用IE的条件注释
            
            <!--[if lt IE 9]><script>...</script><script>...</script><![endif]-->  
            [两个js文件自己google]

# bootstrap表单样式

        创建表单步骤：
        1.创建form标签并添加role="form"(语义化，给浏览器和搜索引擎看)
        2.控制分组，把标签和控件放在一个class为formgroup的div中
        3.给表单控件(input,textarea,select)添加类名form-control
        
## 内联表单
- 给form添加类名form-inline
<!--more-->
## 水平表单
- 给form添加类名form-horizontal
- 给标签label添加类名control-label
- 配合bootstrap网格系统加入类名col-sm-1

## 其它表单控件
- form-control-static：静态表单控件，添加标签和类名，不必用input特定标签
- help-block：表单提示，添加标签和类名（同上）
- 提示图标：glyphicon glyphicon-ok（参照API文档） form-control-feedback
- 按钮：在使用其它类名前均加上基础类名btn

        基础类名：btn
        默认按钮样式：btn-default
        原始按钮样式：btn-primary
        成功按钮样式：btn-success
        链接式按钮：btn-link
        -----------------------
        设置按钮大小
        超大：btn-lg
        默认大小：btn-md
        小号：btn-xs
        btn-block：块级按钮，宽度取决于它父级的宽度的100%
        -----------------------
        设置按钮状态
        激活：active
        禁用：disable

# bootstrap图片样式

## 响应式图片
- img-responsive（max-width:100%）

## 圆角图片
- img-rounded
- img-circle 圆形

## 缩略图
- img-thumbnail：添加一个内边距padding和边框

# bootstrap辅助类
- 左浮动：pull-left
- 右浮动：pull-right
- 块级并居中：center-block 需要设置宽度，不能设浮动
- 强制元素显示/隐藏：show/hide
- 隐藏文字：text-hide

# bootstrap表格样式
- 基础类名：table

        table-striped：斑马线表格
        table-bordered：带边框表格（给td加边框）
        table-hover：鼠标悬停高亮效果
        table-condensed：紧凑型表格（减少单元格padding值）
        table-responsive：响应式表格
        
# bootstrap网格系统

## 原理
- 将容器平分为12份（12列）  
结合媒体查询做出响应式布局效果

## 用法
- 定义一个.row的容器作为行  
定义一个.col的容器作为列  
只有col才能作为row的直接子元素

                    屏幕   屏幕尺寸
        .col-lg-*   超大   >1200px
        .col-md-*   中屏   >992px
        .col-sm-*   小屏   >768px 
        .col-xs-*   超小   <768px
        
        *代表1~12，每一个所占空间大小

## 列偏移&列排序
- 列偏移：不希望两列靠在一起，使用类名.col-\*-offset-\*
- 列排序：设置网格的排列顺序
    - .col-\*-push-\* 往右排
    - .col-\*-pull-\* 往左排
    
            通俗点就是往左移动和往右移动几个网格空间大小
    
# bootstrap下拉菜单
- 创建一个类名为dropdown的div容器，用它来包裹整个下拉菜单
- 在dropdown容器内添加一个按钮button，作为父菜单

        定义类名为dropdown-toggle和自定义属性data-toggle="dropdown"
- 添加按钮里的小三角

        button添加类名为caret的span标签
- 创建下拉菜单

        添加一个ul无序列表，定义类名为dropdown-menu
- 菜单分割线

        添加一个空列表项li，类名为divider

# bootstrap按钮组

        将几个按钮放入一个类名为btn-group的div中
        btn-group-vertical ☞ 垂直按钮组
        按钮组大 ☞ 给组别加类名btn-group-lg|md|sm|xs
- 嵌套按钮组

        在按钮组里面嵌套下拉列表
        
    - 在btn-group里面嵌套一个btn-group，将下拉菜单的父菜单按钮放置在嵌套的btn-group里
    - 给父菜单按钮添加类名dropdown-toggle和自定义属性data-toggle="dropdown"
    - 增加小三角图标`<span class='caret'></span>`
    
# bootstrap导航
- 添加无序列表，用来作为导航
- 给列表添加类名 .nav ☞ 基础类名

        nav-tabs ☞ 表格式导航
        nav-pills ☞ 鼓囊式导航
- 给导航菜单项添加样式

        active ☞ 当前选中项
        disabled ☞ 禁用状态  
          
            
    ☞ 垂直式导航：给导航添加类名nav-stacked
        一般用于鼓囊式导航
    
    ☞ 导航二级菜单：在导航里添加下拉列表
        1. 给父级菜单添加类名dropdown
        2. 在此列表项里添加一个二级菜单列表项 .dropdown-menu
        3. 给此列表里面的a标签添加类名dropdown-toggle和自定义属性data-toggle="dropdown"
        
    ☞ tab标签页导航（选项卡功能）
        1. 添加一个表格式导航
        2. 给导航里面的a标签添加属性data-toggle="tab"的锚点链接地址
        3. 添加一个tab-content的div，在里面包含每一个要切换的tab标签页
        4. 给每一个标签页添加类名tab-pane和fade
        5. 默认显示项
            - 给导航列表项添加类名active
            - 给默认显示标签页添加类名active和in
            
    ☞ 导航条
        导航条头部里面可以放置导航，表单等
        1. 添加类名为navbar的div，用来制作导航条
            navbar-default ☞ 默认
            navbar-inverse ☞ 反色
        2. 在navbar里面添加页面标题
            添加一个类名为navbar-head的div，包含navbar-brand的a标签
        3. 在navbar里添加导航
            在普通导航基础上添加类名navbar-nav
        4. 导航里添加表单（搜索框）
            添加类名navbar-form
            PS：将搜索框和按钮用类名为input-group的div包起来，将搜索按钮放入类名为input-group-btn的span中，可实现搜索框和按钮连在一起的视觉效果
        5. 导航条里的浮动
            navbar-left ☞ 左浮动
            navbar-right ☞ 右浮动
        6. 导航条里面单独的按钮和链接
            按钮 ☞ navbar-btn
            链接 ☞ navbar-link和navbar-text
            普通文字 ☞ navbar-text
        7. 固定导航条
            navbar-fixed-top|navbar-fixed-bottom
    
    ☞ 响应式导航条
        1. 将nav导航用一个类名为collapse和navbar-collapse的div包起来
        2. 在navbar-header里添加类名为navbar-toggle和自定义属性为data-toggle="collapse"与data-target="#myNav（自己取名）"的按钮，在按标签里再加入汉堡按钮
            汉堡按钮：三个span标签，每个类名为icon-bar
        
# bootstrap标签/徽章
- 通过span标签，添加类名label ☞ 基础类名

        label-default
        label-primary
        label-success
        ...
- 通过span标签，添加类名bodge

# bootstrap内置组件

## 缩略图
- 使用网格系统实现

## 警示框

    若在警告框里的文字加链接，则会覆盖原有警示框颜色，应该在a标签里加类名alert-link
- 给警示框加类名alert-dismissable
- 给警示框加类名为close的button标签
- 按钮上加自定义属性data-dismiss="alert"

## 进度条
- 外层div用来写灰色背景，类名progress
    
        加类名progress-striped为条纹进度条
        再加active类名为动态进度条
- 里层div显示进度，类名progress-bar ☞ 基础类名

        progress-bar-success
        ...
- 给progress-bar加行内样式width=百分比

# bootstrap多媒体对象
- 加一个类名为media的div容器
- 在media的div中加一个类名为pull-left的a标签
- 在media的div中添加媒体描述，使用类名为media-body的div
- 给媒体body中的标题加media-heading类名


    要放置多个媒体列表，则在所有列表外套一个类名为media-list的div
    在media-dody中再写入media的div则为媒体嵌套
    
# bootstrap列表组
- 基础列表组

        给无序列表或div加类名list-group，给li列表项加类名list-group-item
- 在列表组里加徽章，bodge，自动的右浮动
- 自定义列表

        li添加标题元素类名为list-group-item-heading放置标题和h标签
        再加入类名为list-group-item-text的p标签来放内容
        
# bootstrap面板

## 基础面板
- 添加类名为panel的div容器，其中panel为基础类名
- 在panel里添加类名为panel-heading的div，在其中添加类名为panel-title的标题h1~h6
- 在panel里添加一个类名为panel-body的div放主内容，表格，表单等
- 在panel-body后添加类名为panel-footer的div，在其中添加普通文字
___

# bootstrap插件
> __以下插件若通过js调用的话，均不必添加任何自定义属性__

## 模态弹出框
> 通俗点就是alert弹出框，只不过样式花哨点

### 结构分析
```text
.modal
    .modal-dialog
        .modal-content
            .modal-header
            .modal-body
            .modal-footer
```
> 模态框默认为隐藏状态

### 触发方式
- 给触发元素（按钮）添加属性data-toggle="modal"和data-target="#myModal（自己取名）"
- a标签加href="#myModal"和data-toggle="modal"
- js触发
    ```javascript
    $('#myModal').modal();
    ```
        给模态框添加动画效果：在modal类名上的div中再增加fade类
        当data-backdrop="static"时，点击modal之外的地方不会使其消失
- 其他参数
    
        通过标签属性和js参数传递，通过js，则去掉data-*属性，只传入后面的名称$('#myModal').modal();只传入modal括号内就好
    - data-backdrop ☞ true|false ☞ 弹出框是否有大背景，默认true
    - data-keyboard ☞ true|false ☞ 按下Esc键是否可以关闭模态框  
    __需要同时设置属性tabindex="-1"__
    
## 滚动监听
- 创建一个导航，添加id属性
- 给导航中的li中的a标签添加href值对应到每一个模块
- 给body添加属性data-spy="scroll"和data-target="#myNavbar（自己取名）"

        固定定位：在需要固定的元素加属性data-spy="affix"和data-offset-top="数值"
        
## 提示框
- 给需要提示的标签添加属性data-toggle="tooltip"，title="提示"
- 通过js调用提示框插件  
    ```javascript
    tooltip();
    ```
- 控制提示框的方向：添加属性data-placement="top|bottom|left|right"

## 弹出框
- 给需要弹出框的元素加属性data-toggle="popover"和data-content="弹出框内容"，title="标题内容"

## 警示框
- 创建一个警示框alert
- 在其中加入关闭按钮
- 用警示框外的按钮来关闭它
    - 在外部元素添加属性data-dismiss="alert"和data-target="#自己取名"

## 按钮
- 模拟单选按钮
    - 在btn-group中添加data-toggle="buttons"
- 模拟复选框
    - 同上，把input的type类型换成checkbox即可
- 按钮状态切换
    - 给button添加属性data-toggle="button"
    - 通过js调用
        ```javascript
        $('selector').button('toggle');
        ```
- 加载状态按钮

        当点击时，按钮状态变为加载中，文本变成data-toggle-text的内容
        
    ```javascript
    $('selector').button('toggle');
    $('selector').button('reset');//写入setTimeout函数中去
    ```
___

## 手风琴插件使用
- 添加一个类名为panel-group的div作为面板组的内容
- 在面板组里面添加面板，并且为面板定义头部和主体内容
- 在panel-title里添加一个a标签，加属性data-toggle="collapse"和data-parent="#面板组id"，href="#面板内容id"
- 将panel-body用类为panel-collapse和collapse的div包起来，并设置id
- 给指定面板加类名in，则为默认展开状态

## 轮播图插件使用
- 添加类名为carousel和slide的div，作为轮播图容器，设置id
- 添加计数器，默认样式为圆点，可用无序列表实现，为其添加类名carousel-indicators，为每个li加属性data-target="#容器id"和data-slide-to="0~n"，对应每一张图
- 添加一个类名为carousel-inner的div容器，用来存放图片，每张图放在类名为item的div中
- 给对应的item项和对应的圆点加active为默认显示的状态
- 添加两个类名为carousel-control的a链接，分别加类名left|right，在其中加属性data-slide="prev"或next，并设置href="#容器id"
- 给carousel加data-ride="carousel"使其自动轮播  
data-interval="毫秒数" ☞ 控制轮播图自动轮播切换间隔时间  
data-wrap="true|false" ☞ 是否循环轮播

        js控制轮播：
        $('selector').carousel();参数同上一条的data属性
        $('selector).carousel('pause|prev|next');暂停|上一张|下一张
        
        轮播事件：
        $('selector').on({
            'slide.bs.carousel':function(){
                ...     切换前事件
            },
            'slid.bs.carousel':function(){
                ...     切换后事件
            }
            })
        
    
