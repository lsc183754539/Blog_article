---
title: 国内访问Github无法显示图片
date: 2020-03-19 06:53:05
tags: [Github,中国防火墙,hosts,图片 ]
categories: [笔记 ]
---

## 问题  
* GitHub打开后图片全为损坏图标，无法加载  

## 解决方法  
* 打开路径C:\Windows\System32\drivers\etc下的hosts文件


```shell  
# GitHub Start  
192.30.253.112 github.com  
192.30.253.119 gist.github.com  
151.101.184.133 assets-cdn.github.com  
151.101.184.133 raw.githubusercontent.com  
151.101.184.133 gist.githubusercontent.com  
151.101.184.133 cloud.githubusercontent.com  
151.101.184.133 camo.githubusercontent.com  
151.101.184.133 avatars0.githubusercontent.com  
151.101.184.133 avatars1.githubusercontent.com  
151.101.184.133 avatars2.githubusercontent.com  
151.101.184.133 avatars3.githubusercontent.com  
151.101.184.133 avatars4.githubusercontent.com  
151.101.184.133 avatars5.githubusercontent.com  
151.101.184.133 avatars6.githubusercontent.com  
151.101.184.133 avatars7.githubusercontent.com  
151.101.184.133 avatars8.githubusercontent.com  
修改hosts文件后，刷新githab页面  
```