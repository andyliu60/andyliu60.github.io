---
title: 个人博客 — Hexo多终端同步篇
date: 2019-01-01 09:45:38
tags:
- Hexo
- GitHub
- Blog
categories:
- 互联网
---
如果需要在多台终端设备上发布博客，那么就需要将Hexo源代码发布到GitHub，并且在多台终端设备之间同步。

# 配置远程仓库 #
1. 在GitHub上创建一个新的分支，例如，分支名称为Hexo

![](/images/21.png)

2. 将Hexo分支设置成默认分支

![](/images/22.png)

# 配置本地仓库 #

1. 注意这里有个巨大的坑！！！如果你用的是第三方的主题theme，是使用git clone下来的话，要把主题文件夹下面把.git文件夹删除掉，不然主题无法push到远程仓库，导致你发布的博客是一片空白

2. 在初次安装Hexo的设备上，初始化博客所在目录

		git init

3. 添加本地所有文件到仓库

		git add -A

4. 添加远程仓库  
我执行该命令后，提示fatal: remote origin already exists.可以忽略该报错。

		git remote add origin git@github.com:yourname/yourname.github.io.git


5. 添加本地仓库分支Hexo

		git branch hexo

6. 将本地Hexo分支的文件强制推送到远程Hexo分支

		git push origin hexo -f

7. 切换到Hexo分支

		git checkout -b hexo

上传完成之后，就会拥有两个远程的分支：master和hexo，其中master是部署成博客的分支；hexo是我们可以clone到其他电脑或其他系统的hexo源文件的分支，而且我们已经将它设置成默认仓库。

# 多终端同步和发布博客 #

1. 在其它终端设备上clone远程分支hexo到本地

		git clone -b hexo git@github.com:yourname/yourname.github.io.git

2. 进入本地仓库执行hexo安装

		npm install

3. 编辑本地博客后，同步到远程hexo分支

		git add "blog files"
		git commit -m "comments"
		git push origin hexo

4. 发布博客

		hexo g -d

