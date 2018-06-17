---
layout:     post
title:      网站修改技巧
subtitle:   server
date:       2018-6-7
author:     Jin
header-img: img/post-bg-hacker.jpg
catalog: true
tags:
    - jekyll
---



## 网站修改技巧
## header 图大小设定
路径：
_layouts/page.html  
```objc
 <header class="intro-header" style="background-image: url('{{ site.baseurl }}/{% if page.header-img %}{{ page.header-img }}{% else %}{{ site.header-img }}{% endif %}');
 width:1500px;height:100px;">
```
 
 ### post 图大小设定
 
 路径：
 _layouts/post.html  
 ```objc
 background-image: url('{{ site.baseurl }}/{% if page.header-img %}{{ page.header-img }}{% else %}{{ site.header-img }}{% endif %}');width:1500px;height:100px;
 ```
### 修改email & 首页图返回键名称
 现在_config.yml文件里修改参数，在以下文件里修改
 
 CNAME路径需要修改，也可以绑定自己的域名
 
  _site/about/index.html
  
  _site/tags/index.html
  都需要更改后上传，然后全关掉视窗，然后重新开机
  
  
 




