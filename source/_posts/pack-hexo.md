---
title: Hexo更换环境或者电脑  
date: 2017-03-05 15:54:30  
categories: "Hexo博客"  
tags: web前端
---

> 当我们更换了环境时，如:  
1、系统重装  
2、更换电脑  
...  
我们需要继续使用Hexo来完成我们的博客写作，该怎么继续？

<!--more-->
在进行博客搬家操作之前，我们需要弄清楚hexo博客部署到github上的一些说明。  

※部署到github上的博客仅仅是你的客观上的能看得到的页面文件，简单说，github上你看到的目录并不是你的hexo文件，而是你的文章文件，及public下的所有目录文件  
※通过clone此目录下的文件到一个新环境下是无法继续我们的原始博客的后续工作的（你如果肯接受你的博客内容为空的话忽略此步说明）  
※支持博客的所有功能只能通过hexo内置的配置文件*.yml

__了解之后着手开始为hexo搬家__

# Git下载并安装

- 打开git bash，在用户主目录下运行：ssh-keygen -t rsa -C "youremail@example.com" 把其中的邮件地址换成自己的邮件地址，然后一路回车
- 最后完成后，会在用户主目录下生成.ssh目录，里面有id_rsa和id_rsa.pub两个文件，这两个就是SSH key密钥对，id_rsa是私钥，千万不能泄露出去，id_rsa.pub是公钥，可以放心地告诉任何人。
- 登陆GitHub，打开「Settings」->「SSH and GPG keys」，然后点击「new SSH key」，填上任意Title，在Key文本框里粘贴公钥id_rsa.pub文件的内容（千万不要粘贴成私钥了！），最后点击「Add SSH Key」，你就应该看到已经添加的Key。

# Node.js下载并安装

自行前往Node.js官网下载稳定版本并且安装到电脑中  
__[https://nodejs.org](https://nodejs.org)__
# Hexo安装

`npm install hexo-cli -g`,`npm install`

# 博客源文件拷贝

> 备份原始文件，有多种方法，其中最简便的为在你github的博客仓库中新建分支hexo，将源文件上传与此，将public生成内容上传于master默认分支  

> 稍微复杂点的措施为：在发布博文之前，先拷贝一份源文件，将其上传到自己github一个新仓库中存储起来  

> 最原始的方法：U盘

若觉得文件过于繁多，仅仅备份  
`_config.yml`，`theme/`，`source/`，`scaffolds/`，`package.json`，`.gitignore`这几个配置文件即可

# 其它组件安装

`npm install hexo-deployer-git –save` hexo发布插件

# 注意

对于博客老用户来说，千万不要使用命令`hexo init`!


