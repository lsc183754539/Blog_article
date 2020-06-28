---
title: Markdown笔记
date: 2019-12-22 17:31:36
tags: [笔记,Markdown]
categories: [笔记 ]
---


# Markdown笔记

## Markdown简介 
> Markdown是一种可以使用普通文本编辑器编写的标记语言，通过简单的标记语法，它可以使普通文本内容具有一定的格式。
>Markdown具有一系列衍生版本，用于扩展Markdown的功能（如表格、脚注、内嵌HTML等等），这些功能原初的Markdown尚不具备，它们能让Markdown转换成更多的格式，例如LaTeX，Docbook。Markdown增强版中比较有名的有Markdown Extra、MultiMarkdown、 Maruku等。这些衍生版本要么基于工具，如Pandoc；要么基于网站，如GitHub和Wikipedia，在语法上基本兼容，但在一些语法和渲染效果上有改动。[^1]
    
[^1]: 引自百度百科 
    
<!--more-->
## Markdown常用软件
1. **在线Markdown编辑器**
* [dillinger](https://dillinger.io/)漂亮强大，支持md、html、pdf文件导出，支持dropbox、OneDrive、Google drive、GitHub等平台。国外网站，可能不稳定
* [MaHua](http://mahua.jser.me/)小众推荐,界面较简洁
* [简书](https://jianshu.com)国内博客平台，自动保存，支持图片拖放生成markdown，需注册账号
* [Cmd Markdown](https://www.zybuluo.com/mdeditor)
    
2. **Chrome插件(谷歌浏览器插件)**
* [Marxico](http://marxi.co/)中文名[马克飞象](https://maxiang.io/)印象笔记不支持Markdown，而这款可以直接把文本存到印象笔记的编辑器对于重度印象笔记用户是个不错的选择。付费软件，可以免费试用
    
3. **Windows平台编辑器**  
* [MarkdownPad](http://www.markdownpad.com/)一款全功能的编辑器，被很多人称赞为Windows平台最好用的markdown编辑器
* [Smark](https://gitee.com/elerao/Smark) 开源软件,本文经由此软件编写，保存的时候有闪退的问题
    
4. **OS X平台**
* [Mou](http://25.io/mou/)老牌的Mac的MD编辑器。
* [MacDown](https://macdown.uranusjr.com/)开源免费
    
## Markdown常用语法
<table>
<tr><td>效果</td><td>Markdown语法</td><td>快捷键</td></tr>
<tr><td>粗体</td><td>`**text**`</td><td>`Ctrl+B`</td></tr>
<tr><td>斜体</td><td>`*text*`</td><td>`Ctrl+I`</td></tr>
<tr><td>链接</td><td>`[title](link)`</td><td>`Ctrl+K`</td></tr>
<tr><td>图片</td><td>`![alt](image link)`</td><td>`Ctrl+Shift+I`</td></tr>
<tr><td>代码</td><td>\`代码\`</td><td>`Ctrl+Shift+K`</td></tr>
<tr><td>代码块</td><td>\`\`\`代码块\`\`\` </td><td></td></tr>
<tr><td>引用</td><td>`> 引用内容 `</td><td>`Ctrl+Q`</td></tr>
</table>
    
### 标题
* h1: `# `
* h2：`## `
* ... ...
* h6: `###### `
    
### 文本样式
* 链接 :`[Title](URL)`
* 加粗 :`**Bold**`
* 斜体字 :`*Italics*`
* 高亮 :`==text==`
* 段落 : 段落之间空一行
* 换行符 : 一行结束时输入4个空格
* 列表 :`* `
* 引用 :`> 引用内容`
* 内嵌代码 :  \` alert('Hello World');\` 
* 画水平线 (HR) :\-\-\-\-\-\-\-\-或`<hr>(占用整行)`
* 方框：\-\ \[\ \] \-
    
### 插入图片
在Markdown的编辑器中输入 `![图片显示不正常时替换成的文本内容](图床链接/图片链接)`    

有些编辑器支持拖放图片自动生成Markdown内容

### 代码
* 内嵌代码：使用\`\`符号将内嵌的代码添加的到中间，如\`code\`
* 代码块：使用后两组\`\`\`将代码块包裹,如\`\`\`code code \`\`\`
    
## 示例
Markdown code: `我们记得[百度](https://www.baidu.com)的链接为www.baidu.com`

效果：我们记得[百度](https://www.baidu.com)的链接为www.baidu.com

Markdown code: `![I Love Markdown](https://ss2.bdstatic.com/70cFvnSh_Q1YnxGkpoWK1HF6hhy/it/u=1613194509,3683268681&fm=26&gp=0.jpg)`

效果：    
![I Love Markdown](https://ss2.bdstatic.com/70cFvnSh_Q1YnxGkpoWK1HF6hhy/it/u=1613194509,3683268681&fm=26&gp=0.jpg)

Markdown code: > 王夫人正过薛姨妈院里坐着，见贾环下了学，命他去抄《金刚经咒》唪诵。那贾环便来到王夫人炕上坐着，命人点了蜡烛，拿腔做势的抄写。一时又叫彩云倒钟茶来，一时又叫玉钏剪蜡花，又说金钏挡了灯亮儿。众丫鬟们素日厌恶他，都不答理。只有彩霞还和他合得来，倒了茶给他，因向他悄悄的道：“你安分些罢，何苦讨人厌。”贾环把眼一瞅道：“我也知道，你别哄我。如今你和宝玉好了，不理我，我也看出来了。”彩霞咬着牙，向他头上戳了一指头，道：“没良心的，‘狗咬吕洞宾——不识好歹。’”

效果：

> 王夫人正过薛姨妈院里坐着，见贾环下了学，命他去抄《金刚经咒》唪诵。那贾环便来到王夫人炕上坐着，命人点了蜡烛，拿腔做势的抄写。一时又叫彩云倒钟茶来，一时又叫玉钏剪蜡花，又说金钏挡了灯亮儿。众丫鬟们素日厌恶他，都不答理。只有彩霞还和他合得来，倒了茶给他，因向他悄悄的道：“你安分些罢，何苦讨人厌。”贾环把眼一瞅道：“我也知道，你别哄我。如今你和宝玉好了，不理我，我也看出来了。”彩霞咬着牙，向他头上戳了一指头，道：“没良心的，‘狗咬吕洞宾——不识好歹。’”
