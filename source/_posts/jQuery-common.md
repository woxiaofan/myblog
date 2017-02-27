---
title: jQuery常用语法
date: 2017-01-06 18:32:56
tags: web前端
---
>__首先附上jQuery官网__  
__[http://jquery.com/](http://jquery.com/)__  
__2.0版本开始放弃了对IE7/8及其之前版本的兼容__


# 准备工作

## 　文件引入
- 必须引入jQuery库文件，引入方法与普通js文件一样

## 　jQuery基本语法
- 单双引号通用
- `$('selecter').function(参数)`
- $符号代表jQuery,是jQuery的缩写
- 隐式迭代：获取一组标签，不需要遍历循环，即可直接操作
- 链式操作：不需要重复获取标签元素，在一个操作后面直接跟另一条命令  
__jQuery每一个操作函数返回值均为object，所以才可以使用链式操作__

# 文档就绪

## 　jQuery文档就绪
- `$(document).ready()`或者简写为：`$(function{})`

## 　与原生JS文档就绪比较
- `window.onload` vs `$(function{})`
- 前者必须等网页中所有的元素（包含图片、flash、视频等）全部加载完毕后执行，而后者等所有的DOM文档结构绘制完毕后即刻执行，不需要等待图片、flash等  
__DOM大标签加载完毕就执行，如p、h、body、div等加载完就执行__
- 一个页面只允许存在一个`window.onload`，而可以存在多个`$(function{})`

# jQuery 选择器<!--more-->

## 　基本选择器
- 标签选择器`$('p')` or `$('div')`
- 类选择器`$('.class')`
- ID选择器`$('#id')`
- 群组选择器`$('div,span,p')`
- 交集选择器`$('p.top')`  
__选取类名为top的p标签__
- 全局选择器`$('*')`

### 　　特殊情况
1. `$(document)`
2. `$(window)`
3. `$('body')`
4. `$(this)`  
__页面中的标签需要加引号或者双引号__

## 　层次选择器
- 后代选择器`$('#box span')`
- 子级选择器`$('#box>span')`
- 紧邻同辈选择器`$('#box+p')`  
__id名为box的后面一个p标签__
- 相邻同辈选择器`$('#box~p')`  
__id名为box的后面所有p标签__

## 　属性选择器
- `$('[name]')`选择所有具有name属性的标签元素
- `$('[name=user]')`所有name=user的标签
- `$('[name!=user]')`name不等于user
- `$('[name^=user]')`以user开头
- `$('[name$=user]')`以user结尾
- `$('[name][id]')`选择同时具有name和id的元素  
__class、type、id等均为属性__

## 　过滤选择器
- :first`$('ul li:first')`
- :last`$('ul li:last')`
- :even  从0开始，选择集合中的偶数行
- :odd  同上，选择奇数行
- :eq(n)  n从0开始计数
- gt(n)  集合中第n个后的元素/大于n的元素，从0开始计数
- lt(n)  同上反
- :not(selector)`$('ul li:not(:eq(3))')`选择不包含selector中的元素
- :header  选择所有h1~h6的标题元素
- :visible  可见元素
- :hidden  不可见元素
- :first-child  列表中的第一个元素，相对于本  身父元素
- :first-of-type  列表中同类型元素
- :nth-c  hild(n)  列表中第n个元素，从1开始计数
- :nth-last-child(n)  倒序计数第n个元素
- :nth-of-type(n)  列表中同类型的第n个子元素，从1开始计数
- :empty  空元素
- :parent  含有子元  素或文本的元素
- :has(selector)`$('div:has(h  2  )')`    匹配包含h2的div
- :contains(text)`$(':contains(hello)')`  匹配包含hello的元素

### 　　常用的过滤方法（function）
1. get(i)  选择第i个元素，返回DOM对象  
__不能采用jQuery写法`$('h2').get(2)`__  
__正确写法：`$('h2').get(2).style.color = 'red'`__
2. eq(i)  选择第i个元素，返回jQuery对象  
__可以采用jQuery写法`$('h2').eq(2)`__   
__正确写法：`$('h2').eq(2).css('color'`,'red')__
3. first()|last()  选择第一个|最后一个元素
4. not(selector)  同not选择器
`$('h2').not(':contains(hello)')`
5. has()  同has选择器
6. find(selector)  获取当前匹配元素集合中每一个元素的后代，同has选择器，但返回的是find中的标签，而不是像has的父级元素

## 　表单选择器
- :input  表单元素，包括input、textarea、select、button
- :text  单行文本框元素，只能匹配type=text的文本框
- :password
- :radio  单选按钮
- :checkbox  复选框
- :submit  type=submit和button标签
- :image  type='image'的input图像域
- :reset
- :button
- :file
- :checked
- :focus  焦点所在元素

# DOM对象和jQuery对象

## 　jQuery对象转化成 DOM对象
- jQuery对象可以理解为由DOM元素组成的一个数组
- get(i)  
jQuery对象.get(i)
- jQuery对象[i]  
因为通过jQuery获取的对象类似于一个数组

## 　DOM对象转化成jQuery对象
- 将DOM获取到的对象变量用小括号包起来，前面加$  
$(DOM对象)


# jQuery事件

## 　jQuery常用事件

### 　　鼠标事件
- 点击事件
    - click
    - dblclick  双击
    - mousedown
    - mouseup  
- 移动事件
    - mouseover 移入该元素和对应的子元素
    - mouseout  移出该元素和对应的子元素
    - mouseenter    移入该元素，不对其子元素生效
    - mouseleave    移出该元素，不对其子元素生效
    - mousemove 鼠标每移动一个像素就会触发一次
- 组合事件
    - hover  
    mouseenter+mouseleave  
    jQuery1.8版本之后改为mouseover+mouseout
    
### 　　键盘事件
- keydown
- keyup
- keypress  产生可打印的字符时触发，不包括中文

### 　　表单事件
- focus 获得焦点
- submit
- blur  失去焦点
- change

## 　事件绑定与移除

### 　　事件绑定
- 直接通过事件名绑定  
`$(selector).事件名()`
- bind()  
    - 绑定一个事件：bind('事件类型',function(){});同直接绑定
    - 绑定多个事件：  
    $(selector).bind({事件类型1:function(){},事件类型2:function(){},...})  
    __绑定一个事件：每用一次事件查找一次__  
    __绑定多个事件：只需要查找一遍元素__
- one()  
绑定一次性事件，比如按钮点击后自动不再具有点击效果，写法同bind绑定
- on()  
类似于bind绑定，比bind多一个参数(selector)，可实现动态更新事件（页面加载完后新增加的元素也可实现此事件方法，而bind无法响应页面加载后新增的元素）  
```javascript
    $('ul').on('click','li',function(){
        alert($(this).text);
    });                         //动态绑定
    $('ul li').bind('click',function(){
        alert($(this).text);    //静态绑定
    });
```

### 　　事件移除
- unbind()  
不传参数，则默认移除所有事件  
unbind([type],[function])
    - 一个参数：可以指定移除事件类型
    - 两个参数：可以指定移除某个事件其中的某个响应方法
- off()  
同on()相对应

### 　　事件的命名空间
- 在bind绑定事件中，在事件类型中，使用事件类型命名来创建同一个事件的多个名字，如click.a,click.b...  
__命名空间后要加引号，如'click.a','click.b'__

## 　模拟事件
- trigger()  
自动触发事件，传入参数为事件类型  
链式写法：`$(selector).trigger('事件类型')`
- triggerHandler()  
同上，区别为：
    - 不会执行事件的默认行为，比如表单的功能按钮和链接标签
    - 只触发jQuery对象集合中的第一个元素的事件处理函数，比如无序列表下的li集合，只触发第一个li
    - 返回值为undefined，trigger返回jQuery对象，无法继续在其后增加链式操作
    - 阻止了事件冒泡  
    使用传入事件event参数  
    `event.stopPropagation()`也可以达到阻止事件冒泡功能
    
## 　event对象
>event只有事件处理函数能够访问，当事件处理完毕后，event就会自动销毁

### 　　event常用属性
- type
- clientX|clientY  
窗口可视化区域x和y坐标
- pageX|pageY  
相对于文档的x和y坐标，y坐标算上滚动条坐标
- offsetX|offsetY  
相对于事件源的坐标，在哪个标签内就获取这个标签内的x，y坐标
- screenX|screenY  
屏幕的x，y坐标
- keyCode  
检测键盘事件相对应的内码
- target  
返回触发该事件的DOM元素  
比如标签h、p、div...元素

### 　　event常用方法
- `preventDefault()`  
阻止默认行为
- `stopPropagation()`  
阻止事件冒泡行为

# jQuery动画
- 显示/隐藏
    - `show()`  `hide()`  
    可传入参数：'slow'、'normal'、'fast'，或者毫秒数
    - `toggle()`  
    一个按钮两种方式切换，再点击可隐藏
- 淡入/淡出
    - `fadeIn()`    `fadeOut()`  
    不传参数有默认动画，但速度很快
    - `fadeToggle`  
    同`toggle()`
- 改变元素高度
    - `slideUp()`高度由大到小  
    `slideDown()`高度由小到大
    - `slideToggle()`  
    同`toggle()`
- 自定义动画
    - `animate(param,speed,easing,callback)`  
    param：改变css一组样式属性名称和值得集合，只有数值型的属性可执行  
    speed：'slow'、'fast'，或者毫秒数  
    easing：'linear'匀速、'swing'由快到慢  
        __操作动画的方法：__  
        - `stop()`停止元素正在执行的动画`暂停`
        - `finish()`立即结束动画立刻到达动画的终点`结束`
        - `delay()`延迟执行动画效果
        
# jQuery样式操作

## 　样式设置与获取
- 获取样式`$(selector).css(属性名称)`传一个参数  
返回的为字符串类型，带有属性自带的单位值
- 设置样式`$(selector).css({'color':'red','font':'16px',...})`

>__在jQuery中设置数值类型样式可省略引号与单位,样式名称也可去掉引号，但遇到长单词需改用驼峰写法__

## 　通过类名来控制样式
- `addClass('className')`添加样式，通过类名增加样式  
多个类名：`addClass('className1' 'className2' ...)
- `removeClass()`方法同上，移除类名
- `toggleClass()`切换类名

## 　快速获取和设置样式
- `.width()` `.height()`  
返回number类型，若传参，则为设置宽度和高度
- `innerWidth()` `innerHeight()`  
设置和获取元素的内宽度和内高度，包含padding，不含margin和border
- `outWidth()` `outHeight()`  
设置和获取元素的外高度和外宽度，包含padding和border  
当传入参数为true，返回值包含margin
- `offset()`  
设置或返回一个元素相对于文档的left和right，返回的是left和right的对象集合
- `position()`  
相对于该元素的父元素的left和right
- `scrollTop()` `scrollLeft()`  
设置于滚动条顶部和左部的偏移  
```javascript
    $('html,body').scrollTop();//设置,IE+FF为html，chrome为body
    $(window).scrollTop();//获取
```

# jQuery内容和属性操作
- `html()`类似于原生js中的innerHtml  
```text
    获取和设置元素的内容，包含HTML标签
    将HTML标签和里面的文字以字符串形式完全获取出来
    比如段落内为hello，获取到的返回值为<p>hello</p>
```
__传入参数，即改为设置新内容，会覆盖原先的内容__
- `text()`类似于原生js里的innerText  
获取和设置元素内的文本内容，不含html标签，内容为hello的段落，获取到的返回值为hello  
__传入参数，即为设置新内容，会覆盖原先的内容__
- `val()`同原生js中的`value()`
- `attr()`元素属性  
    - 传入一个参数，获取属性
    - 两个参数，设置单个属性`attr(name,value)`
    - 多个参数，设置多个属性
    - `removeAttr()`移除属性，传入属性名称即可
- `prop()`类似于`attr()`  
主要作用于select、radio、checkbox，选中则返回true  
`removeProp()`移除属性

# jQuery对于节点的操作

## 　创建节点
- `$(selector)`通过选择器获取节点
- `$(element)`把dom节点转换成jQuery节点
- `$(html代码)` `$('<p>hello</p>')`

## 　在元素内部插入节点
- `append()` a.append(b) b元素插入到a元素中
- `appendTo()`
- `prepend()`
- `prependTo`

## 　在元素外部插入节点
- `after()` a.after(b) b元素插入到a元素的后面
- `insetAfter()`
- `before()`
- `insetBefore()`

## 　包裹节点
- `wrap()`将所匹配的元素用其他元素包裹起来
- `unwrap()`移除一个元素的父元素
- `wrapAll()`将所有元素用一个标签包裹起来
- `wrapInner()`将匹配的元素的子元素（包含节点和文本）用其他元素包裹

## 　替换节点
- `a.replaceWith(b)`把a元素替换成b元素
- `a.replaceAll(b)`同上反

## 　克隆节点
- `clone()`  
用于复制节点，复制出的节点不带有原有元素的事件，当传入参数为true时，复制元素并复制原有的事件

## 　删除节点
- `remove()`
- `detach()`删除节点，保留原有数据和事件，同`clone(true)`
- `empty()`清空节点内的内容，不删除此节点

# jQuery遍历元素

## 　　获取同辈元素
- `next()`获取紧邻元素后面的元素
- `nextAll()`获取元素后面所有同级元素
- `prev()`紧邻前面一个元素
- `prevAll()`元素前面所有元素
- `siblings()`元素前后所有同级元素

## 　　获取前辈元素
- `parent()`获取元素的父级元素(从父级开始遍历)
- `parents()`获取元素所有的祖先元素(从父级开始遍历)
- `closest()`参数必传，获取匹配选择器的第一个祖先元素(从自身开始遍历)

## 　　获取子元素
- `children()`获取一个元素的所有子元素，但是不包含子元素的子元素
- `find(selector)`获取所有匹配元素的子元素
- `contents()`当前所有的子节点（文本节点+注释节点）一般用于获取iframe框架内容

## 　　遍历
- `each()`对jQuery对象进行迭代，为每一个元素执行函数  
```
each(function(index,element) {
  ...
})
```
- `index()`获取元素的下标位置
- `is()`判断当前元素是否符合选择器的条件，必传参数selector，匹配成功则返回true

# jQuery插件封装
- `$.extend()`
    - 一个参数：用于扩展jQuery类本身，为jQuery类添加新方法
    ```text
       $.extend({
          'functionName1':function(){
              ...
          },
          'functionName2':function(){
              ...
          },
          ...
     })   
    ```
    - 多个参数：用于合并对象
        - 浅拷贝：第一个参数可以传入空对象，那么原来的值就不会被后面的对象覆盖  
        `$.extend(obj1,obj2,obj3...)`
        - 深拷贝：第一个参数传入true  
        对象内包含对象，则会进行合并，并不会覆盖值
- `$.fn.extend()`  
用来扩展$元素的对象的方法
- jQuery命名冲突
    > 当另一个js插件库中也有$符号的存在，则会发生名字冲突
    
    `jQuery.noConflict()`放弃jQuery对命名的使用权
    - 将$全部用全称jQuery代替
    - 用新的变量作为$符号使用`var $$=jQuery`
    - 使用代码块，在代码块中仍可使用$符号
    > 插件库命名规范：jQuery.插件名字.版本号.js

***

# jQuery-ajax

## 　　ajax简易方法
- `$.get(url,data,callback,type)`  
dada：需要发送的参数{key:value}  
callback：指定成功时的回调函数  
type：指定返回内容的格式（xml，html，script，json，string）  
- `$(selector).load(url)`加载html，不需要回调函数即可加载到所选元素中
- `$.getScript()`加载脚本文件
- `$.getJSON`加载json文件
- `$.ajax()`
    ```
       $.ajax({
         'type':'get',
          'url':'',
          async:true,  //默认为true，可不写
          data:{},    //发送到服务器的数据
          dataType: ,   //预期服务器返回的数据类型
          success:callback,
          error:callback,
          ...
     })   
    ```

## 　　ajax参数详解
- type 请求方式，默认为get
- url
- data key:value格式
- dataType 返回的数据类型，如：json，不指定则jQuery自动断定
- cache 是否缓存，默认为true，当dataType为script与jsonp【跨域用途】时cache默认false
- global 是否触发ajax全局事件，默认true
- jsonpCallback 为jsonp请求指定一个回调函数的名称
- context 用于指定`$(this)`所指向的对象
- success 请求成功时所执行的操作function
- error 失败时，同上
- complete function函数，请求完成后执行，不管成败  
success:function(data,textStatus,xhr)  
error:function(xhr,textStatus,errormsg)  
complete:function(xhr,textStatus)  
    ```text
        data：请求地址返回的数据
        textStatus：请求状态的文字说明
        xhr：xmlHTTPRequest对象
    ```
- beforeSend function(xhr)发送请求之前调用
- username|password 响应HTTP访问认证请求的用户名和密码

## 　　ajax全局设置
> 用于设置全局ajax默认选项（当需要多次使用ajax请求时，有些默认参数是一样的，可以通过全局一次性设置）  
$.ajaxSetup({同ajax参数})  
设置后不会发送请求，只是设置，所以`$.ajax()`还是要写一遍

- 全局事件：  
`$(document).ajaxComplete(function(){});`  
`$(document).ajaxSuccess(function(){});`  
`$(document).ajaxError(function(){});`  
`$(document).ajaxStart(function(){});`  
`$(document).ajaxSend(function(){});`  
`$(document).ajaxStop(function(){});`  
__function内参数为：event，xhr，options__

# 序列化数据 
    使用序列化方法时表单必须加一个name属性  
    serialize() 序列化表单内容，将表单内容转化为字符串  
    serializeArray() 序列化表单内容，返回数据格式
    
# jQuery-jsonp跨域
> 同源策略：浏览器不能向不同域的地址提交请求

## 　　远程获取数据
- script的src属性
- img的src属性
- iframe的src属性

## 　　jsonp跨域
- 可以让网页从别的域名（网站）获取资料，只支持get请求  
设置☞  
dataType:'jsonp',  
jsonpCallback:'自己命名(服务器的function名称，不传参数，服务器会自动生成一个随机名)'
    


          

