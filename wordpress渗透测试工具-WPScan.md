---
title: wordpress渗透测试工具-WPScan
date: 2020-03-31 15:38:33
tags: [kali,渗透测试,wordpress,WPScan ]
categories: [笔记,渗透测试 ]
---
# WPScan 简介
* WPScan是一个扫描 WordPress漏洞的黑盒扫描器，它可以为Web开发人员扫描WordPress漏洞。它是一款非常棒的Web服务器评估工具，我认为这个工具应该成为所有针对WordPress网站进行的渗透测试的一部分。
> ## WordPress介绍
>* WordPress是全球流行的博客网站，全球有上百万人使用它来搭建博客。他使用PHP脚本和Mysql数据库来搭建网站。
>* Wordpress作为三大建站模板之一，在全世界范围内有大量的用户，这也导致白帽子都会去跟踪 WordPress的安全漏洞，Wordpress自诞生起也出现了很多漏洞。Wordpress还可以使用插件、主题。于是Wordpress本身很难挖掘什么安全问题的时候，安全研究者开始研究其插件、主题的漏洞。通过插件，主题的漏洞去渗透Wordpress站点，于是WPScan应运而生，收集 Wordpress的各种漏洞，形成一个Wordpress专用扫描器。  
* WPScan是Kali Linux默认自带的一款漏洞扫描工具，它采用Ruby编写，能够扫描WordPress网站中的多种安全漏洞，其中包括WordPress本身的漏洞、插件漏洞和主题漏洞。最新版本WPScan的数据库中包含超过18000种插件漏洞和2600种主题漏洞，并且支持最新版本的WordPress。值得注意的是，它不仅能够扫描类似robots.txt这样的敏感文件，而且还能够检测当前已启用的插件和其他功能。
* 该扫描器可以实现获取站点用户名，获取安装的所有插件、主题，以及存在漏洞的插件、主题，并提供漏洞信息。同时还可以实现对未加防护的Wordpress站点暴力破解用户名密码。