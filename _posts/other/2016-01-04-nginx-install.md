---
layout: post
title: nginx study-install
category: other
---

2015-12-08

##  nginx环境搭建（unbutn）

>  今天学习一下nginx,首先就是环境搭建了，用公司的一台unbutn系统的电脑，试着自己去安装一下。（吭还不少呢）

###  下载nginx

下载的地址是：[nginx](http://nginx.org/)
也可以百度nginx点击进去nginx news网站如下图
![百度nginx图片](http://i.niupic.com/images/2016/01/05/dlsfgK.png)

>  一直忙着淘宝天猫抓取，这个都快忘了。。

### 安装nginx

```shell
  $ ./configure (编译)这个敲一下命令就可以了，但是一般编译很可能出错，我当时就缺少prel的模块,有可能还会有gc++模块，反正你configure之后，看看缺少什么，那就添加什么模块。
  这时候你可能需要去添加缺少的模块， Unbutn 用apt-get或者去下载模块。
```
>   看这篇教程吧，自己nginx很菜，http://seanlook.com/2015/05/17/nginx-install-and-config/
