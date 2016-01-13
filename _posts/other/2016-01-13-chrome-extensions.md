---
layout: post
title: nginx study-install
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
