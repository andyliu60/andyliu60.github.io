---
title: str和repr
date: 2018-12-05 15:07:21
tags:
- Python
categories:
- 编程
---
str函数和repr函数是将值转换为字符串的两种机制。

**str函数：把值转换为合理形式的字符串，以便用户可以理解。**

**repr函数：它会创建一个字符串，以合法的Python表达式的形式来表示值。**

str例子：

		>>> s = 'Hello, world!'
		
		>>> print str(s)
		Hello, world!
		
		>>> print str(2.0/11.0)
		0.181818181818

repr例子：

		>>> s = 'Hello, world!'
		
		>>> print repr(s)
		'Hello, world!'

		>>> print repr(2.0/11.0)
		0.18181818181818182