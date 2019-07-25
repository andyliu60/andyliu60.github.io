---
title: Hexo-Next主题添加搜索功能
date: 2019-07-25 16:21:25
tags:
- Blog
- Hexo
categories:
- 互联网
---
# 安装插件

在博客根目录下执行以下命令：

	$ npm install hexo-generator-searchdb --save


# 配置Hexo


安装完成，编辑博客配置文件：**_config.yml**，在配置文件的任意位置添加以下内容。

	search:
	  path: search.xml
	  field: post
	  format: html
	  limit: 10000

# 配置Next主题

Next 主题自带搜索设置，编辑主题配置文件：**_config.yml**

找到文件中 **Local search** 的相关配置，设为 **true**

	# Local search
	local_search:
	  enable: true

# 部署博客

	hexo g -d