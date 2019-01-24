---
title: Git命令显示中文乱码问题
date: 2019-01-05 15:10:22
tags: 
- RaspberryPi
categories:
- 智能家居
---

使用Git命令时，中文显示为乱码。

```
$ git status
On branch hexo
Your branch is up to date with 'origin/hexo'.

Untracked files:
  (use "git add <file>..." to include in what will be committed)

	"\346\240\221\350\216\223\346\264\276\346\214\202\350\275\275\347\247\273\345\212\250\347\241\254\347\233\230.md"

nothing added to commit but untracked files present (use "git add" to track)

```

解决方法

在命令行中输入以下命令：

```
git config --global core.quotepath false
```

```
$ git status
On branch hexo
Your branch is up to date with 'origin/hexo'.

Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

	new file:   树莓派挂载移动硬盘.md
```