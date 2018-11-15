---
title: 个人博客 — Hexo安装篇
date: 2018-11-07 13:47:15
tags:
- Hexo
- Blog
categories:
- 互联网
---
# 什么是Hexo? #

[Hexo](https://hexo.io/)是一个快速、 简单和强大的博客框架。你可以用Markdown或者其它语言撰写博客内容，Hexo会自动生成静态文件。


# 如何在Windows上安装Hexo? #

	
1. 下载并安装[Node.js](https://nodejs.org/en/)。	 
2. 下载并安装[Git](https://git-scm.com/download/win)。 <!-- more -->
3. 安装Hexo。  
在桌面上点击右键，选择“Git Bash Here” 。在命令行窗口中，输入以下命令（告警信息可以忽略）：  
![](/images/01.png)  
  
		npm install -g hexo-cli  
  
![](/images/02.png)  

4. 验证Hexo安装成功。  
在Git Bash窗口中，输入以下命令，可以看到Hexo的版本信息。


![](/images/03.png)

5. 初始化设置Hexo

        hexo init <folder>
        cd <folder>
        npm install  
  
![](/images/04.png)  
![](/images/05.png)

6. 设置语言  
用记事本打开_config.yml， 设置language参数。  

		language: zh-CN

7. 修改主题  
  
		git clone https://github.com/theme-next/hexo-theme-next themes/next  
![](/images/06.png)    
  用记事本打开_config.yml， 设置theme参数。
  
  		theme: next  
  
8. 访问博客  
在Gib Bash窗口中，运行命令  
  
		hexo server    
![](/images/07.png)  
打开浏览器，输入URL: http://localhost:4000  
![](/images/08.png)




            
