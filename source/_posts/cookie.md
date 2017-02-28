---
title: cookie的常用操作  
date: 2017-02-27 11:58:54  
tags: web前端  
categories: cookie   
---
> JavaScript是运行在客户端的脚本，因此一般是不能够设置Session的，因为Session是运行在服务器端的。而cookie是运行在客户端的，所以可以用JS来设置cookie。


假设有这样一种情况，在某个用例流程中，由A页面跳至B页面，若在A页面中采用JS用变量temp保存了某一变量的值，在B页面的时候，同样需要使用JS来引用temp的变量值，对于JS中的全局变量或者静态变量的生命周期是有限的，当发生页面跳转或者页面关闭的时候，这些变量的值会重新载入，即没有达到保存的效果。解决这个问题的最好的方案是采用cookie来保存该变量的值，那么如何来设置和读取cookie呢？

首先需要稍微了解一下cookie的结构，简单地说：cookie是以键值对的形式保存的，即key=value的格式。各个cookie之间一般是以“;”分隔。

# JS设置cookie

假设在A页面中要保存变量username的值("yyf")到cookie中,key值为name，则相应的JS代码为：

```javascript
document.cookie = "name=" + yyf;
```

假设需要加上过期时间，方法如下：
```javascript
function setCookie(name,value){
    var Days = 30;
    var exp = new Date();
    exp.setTime(exp.getTime() + Days*24*60*60*1000);//时间戳以毫秒为单位
    document.cookie = name + "="+ escape (value) + ";expires=" + exp.toGMTString();
}
```

# JS读取cookie<!--more-->

假设cookie中存储的内容为：username=yyf;password=123

则在B页面中获取变量username的值的JS代码如下：
```javascript
var username=document.cookie.split(";")[0].split("=")[1];
//则该username获取结果为yyf
```

    注意：上述方法仅指明确cookie的数据数目和顺序的情况下才可使用，比如自己设置的或者通过浏览器查看后的页面。若是一个陌生页面，则应该通过如下万能法
    
```javascript
function getCookie(cName){
    var cookieArr = document.cookie.split(";");//将cookie通过分号分割，存为一个名为cookieArr的数组
    for (var i=0; i < cookieArr.length; i++){
        var cookieVal = cookieArr[i].split("=");//遍历数组，将每一个cookie的key和value通过等于号分割，存为一个名为cookieVal的数组
        if (cName == cookieVal[0])
        return unescape(cookieVal[1]);//将value值解密后拿出
    }
    return null;
}
```

# 删除cookies

```javascript
function delCookie(name){
    var exp = new Date();
    exp.setTime(exp.getTime() - 1);//将本地时间戳设置为不存在的一个时间即可
    var cval=getCookie(name);
    if(cval!=null)
    document.cookie= name + "="+cval+";expires="+exp.toGMTString();
}
```
___

# jQuery-Cookie插件  

> jQuery.cookie.js是个很好的cookie插件，包括设置、删除、获取等一系列完整的cookie操作

- 创建会话cookie（Session cookie，既浏览器内存cookie，浏览器关闭后自动删除）

```javascript
$.cookie('the_cookie', 'the_value');
```

- 创建一个生生存周期为7天的cookie

```javascript
$.cookie('the_cookie', 'the_value', { expires: 7 });
```

- 创建一个有期限的cookie，整个站点可以读取

```javascript
$.cookie('the_cookie', 'the_value', { expires: 7, path: '/' });
```

- 读取cookie

```javascript
$.cookie('the_cookie'); // => "the_value"
$.cookie('not_existing'); // => undefined
```

- 读取所有可用cookie

```javascript
$.cookie(); // => { "the_cookie": "the_value", "...remaining": "cookies" }
```

- 删除cookie

```javascript
// 找到指定的cookie返回true，否则返回false
$.removeCookie('the_cookie');
// 删除指定过path的cookie
$.removeCookie('the_cookie', { path: '/' });
```

    $.cookie(’name’, ‘value’, {expires: 7, path: ‘/’, domain: ‘jquery.com’, secure: true});
    
    (1)读取cookie值
    　　　$.cookie(cookieName)  cookieName:要读取的cookie名称。
         示例：$.cookie("username"); 读取保存在cookie中名为的username的值。
    (2)写入设置Cookie值：
    　　　$.cookie(cookieName,cookieValue);  cookieName:要设置的cookie名称，cookieValue表示相对应的值。
    　　　示例:$.cookie("username","admin"); 将值"admin"写入cookie名为username的cookie中。
    　　　　　 $.cookie("username",NULL);　　　销毁名称为username的cookie
    (3)[option]参数说明：
    　　  expires:　　有限日期，可以是一个整数或一个日期(单位：天)。　　这个地方也要注意，如果不设置这个东西，浏览器关闭之后此cookie就失效了
    　　　 path:　　　 cookie值保存的路径，默认与创建页路径一致。
          domin: cookie域名属性，默认与创建页域名一样。　　这个地方要相当注意，跨域的概念，如果要主域名二级域名有效则要设置　　".xxx.com"
          secrue:　　 一个布尔值，表示传输cookie值时，是否需要一个安全协议。
    
[另外更多操作详情点击API文档](https://github.com/carhartl/jquery-cookie#readme)