---
title: PHP<5.3.4版本上传路径%00截断漏洞绕过文件白名单
date: 2020-05-24 08:50:58
tags: [渗透测试,shell,文件上传漏洞 ]
categories: [渗透测试 ]
---

## 准备工具
* burpsuite
* 浏览器
* php webshell file
<!--more-->
## 编写php文件，作为漏洞测试使用
```php
<?php eval(@_post[pp]); ?>
<?php phpinfo(); ?>
```
# 复现
* 使用burpsuite监听拦截8080端口
* 浏览器代理设置为localhost:8080
* 尝试在页面上传webshell文件
* 回到burpsuite ，将上传的数据包右击>发送到重放  ![](https://imgkr.cn-bj.ufileos.com/d96c09d4-730d-4551-b190-11d0361df887.png)
* 将文件名更改为filesname.php .jpg（有个空格，方便寻找其他也可）  ![](https://imgkr.cn-bj.ufileos.com/5e1ee433-4610-47c5-9127-187087a53392.png)
* 切换到hex选项卡，找到空格（或是你的符号）的十六进制，更改为00  ![](https://imgkr.cn-bj.ufileos.com/1212734e-d050-4371-aa15-c027b7f15f66.png)
* 将流量重放，查看返回结果，并利用解析漏洞尝试连接  ![](https://imgkr.cn-bj.ufileos.com/026830b5-407e-407a-99a6-16a2648f7a2d.png)  ![](https://imgkr.cn-bj.ufileos.com/5db3a841-2d2c-42fb-b576-4043cfac4324.png)