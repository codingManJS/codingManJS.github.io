---
layout: post
title: chrome 插件学习
category: other
---

2016-01-13

### chrome插件开发
>  最近一直做淘宝天猫抓取，各种问题，最后采用插件的方式抓取数据，下面就来介绍一下chrome插件的开发。

#### 插件开发目录

-----

  -js
  -css
  -lib
  -background.js
  -manifest.json
  -content_script.js
  -popup.html
  -popup.js

-----

###  chrome插件开发第一步就是配置mainfest.json

```javascript
{
  "manifest_version": 2,//一般建议写2
  "name": "我的应用",// app
  "version": "版本字符串", //v 1.0.0
  "permissions":[]//这个很重要，这个是开启一些权限的比如storage，tabs，fileSystem等等
  "background": {
      "scripts": ["jquery.js","background.js"]
  },//一般叫background.js
  "content_scripts": [{
      "matches": ["https://*.taobao.com/*","https://*.tmall.com/*", "http://item.jd.com/*"],
      "js": ["jquery.js","myscript.js"]
  }],//content_scripts
  "browser_action": {
      "default_icon": "icon.png",
      "default_popup": "popup.html"
  },
}

```

###  数据交流

>  chrome插件中background，content_script, popup ,server4个部分之间如何数据交流？看下图

![chrome 插件数据交流图解](http://chuantu.biz/t2/24/1452679544x1822611273.png)

  其中可以看出background是重要的，这个相当于一个数据交流的中心。popup其实可以用chrome.extension.getBackgroundPage()获取background，所以他可以获取background上所有的东西，concontent_script和background通过sendMessage来通讯，整个chrome插件通过background来和server数据交流。

### 代码


写代码的话基本js吧，popup是你的插件交互用的界面，会用一些html，css之类的饿，基本上js就可以写好了，如果可以话 angularjs来做也可以，这里有个例子


```

  $  git clone git://github.com/GoogleChrome/chrome-app-codelab.git


```


还要注意chrome给的一些api，比如上面的sendMessage,getBackgroundPage。等等
可以看这个网站，中文的很好
 https://crxdoc-zh.appspot.com/apps/about_apps
