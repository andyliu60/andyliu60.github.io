---
title: 将Win32安装程序转换为MSIX格式
date: 2019-02-13 12:14:09
tags:
- Intune
categories:
- 企业产品
---
MSIX是微软应用程序的一种格式。

通过使用**MSIX Packaging Tool**转换工具，可以将Win32的安装包，如.exe,.msi安装文件，转化为MSIX格式的软件包。

1. 可以在微软商店中下载**MSIX Packaging Tool**

![](/images/153.png)

2. 打开软件。

![](/images/154.png)

3. 选择“Application Package”，上传文件。

![](/images/155.png)

4. 点击Next，选择“Create package on this computer”。

![](/images/156.png)

5. 点击Next，确保根据要求填写Package Name, Publisher Name和Version。

![](/images/157.png)

6. 点击Next，安装**MSIX Packaging Tool Driver**。

![](/images/158.png)

7. 点击Next，开始安装7-Zip

![](/images/159.png)
![](/images/160.png)

8. 点击Next，

![](/images/161.png)

9. 选择“Yes, move on”

![](/images/162.png)

10. 选择MSIX文件的保存路径，点击Create。

![](/images/163.png)

11. 点击Close。

![](/images/164.png)

12. 查看生成的文件。

![](/images/165.png)


> 注：在转换Snagit.exe文件的时候，转换失败，并出现以下截图中的错误。

> ![](/images/166.png)

> 查看日志文件，发现以下错误信息。

> [2/13/2019 11:24:18 AM] [Error] E R R O R :   P R I 1 9 1 :   0 x 8 0 0 8 0 2 0 4   -   A p p x   m a n i f e s t   n o t   f o u n d   o r   i s   i n v a l i d .   P l e a s e   e n s u r e   w e l l - f o r m e d   m a n i f e s t   f i l e   i s   p r e s e n t .   O r   s p e c i f y   a n   i n d e x   n a m e   w i t h   / i n   s w i t c h . 
[2/13/2019 11:24:18 AM] [Error]  
[2/13/2019 11:24:18 AM] [Error]  e r r o r   C 0 0 C E 1 A 1 :   A p p   m a n i f e s t   v a l i d a t i o n   e r r o r :   T h e   a p p   m a n i f e s t   m u s t   b e   v a l i d   a s   p e r   s c h e m a :   L i n e   2 0 ,   C o l u m n   1 3 7 5 6 ,   R e a s o n :   ' 1 4 2 7 2 5 0 4 - e 2 b e - 4 9 7 6 - a 4 7 c - 7 a e e 1 7 1 1 c 6 9 0 '   i s   a   d u p l i c a t e   k e y   f o r   t h e   u n i q u e   I d e n t i t y   C o n s t r a i n t   ' { h t t p : / / s c h e m a s . m i c r o s o f t . c o m / a p p x / m a n i f e s t / f o u n d a t i o n / w i n d o w s 1 0 } C l a s s _ I d ' . 
[2/13/2019 11:24:18 AM] [Error]  
[2/13/2019 11:24:18 AM] [Error]  
[2/13/2019 11:24:18 AM] [Error]  
[2/13/2019 11:24:18 AM] [Error]  
[2/13/2019 11:24:18 AM] [Error]  
[2/13/2019 11:24:18 AM] [Error]  
[2/13/2019 11:24:18 AM] [Error]  
[2/13/2019 11:24:18 AM] [Error]  
[2/13/2019 11:24:18 AM] [Error] makepri.exe failed, exit code = -2146958844
[2/13/2019 11:24:18 AM] [Error] Error occurred: Microsoft.Packaging.SDKUtils.ProcessRunner.ProcessRunnerException: Process makepri.exe failed with exit code -2146958844.

> 根据以下帖子的讨论，这个问题可能是转换工具的软件Bug。
> 
> [https://techcommunity.microsoft.com/t5/MSIX-Packaging-and-Tools/Process-makepri-exe-failed-with-exit-code-2146958844/m-p/281091](https://techcommunity.microsoft.com/t5/MSIX-Packaging-and-Tools/Process-makepri-exe-failed-with-exit-code-2146958844/m-p/281091)



参考资料：

[https://docs.microsoft.com/en-us//windows/msix/](https://docs.microsoft.com/en-us//windows/msix/)