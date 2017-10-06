---
layout: post
title: 如何解决windows出现的runtime error C:\WINDOWS\explorer.exe问题
date: 2017-10-06
tags:
- bug
- 系统错误
categories: 
- windows
description: windows会经常出现Visual C++ Runtime Errors这样的错误，这篇博客解决的是这类错误中的C:\Windows\Explorer.EXE问题。
---

### 为什么会出现 runtime Error 的错误？
我分析了一下，大概有以下几个原因：
>* Microsoft Visual C++ 有些版本被删除或是新旧版本有冲突。
>* 系统更新不完整或是删除/复制不完整导致的文件损坏。
>* 病毒或是木马攻击了你的电脑，所以在看下面的修复教程之前，你可以先试着杀毒。
<!-- more -->
### runtime Error中的C:\Windows\Explorer.EXE
这个错误我也不确定是怎样产生的，但是确实比较坑，桌面一直弹出这个界面：<br>
![image](https://github.com/Lihit/Lihit.github.io/blob/master/assets/img/2017-10-06-solve-runtime-error-of-windows/Visual_C___error_preview.png)
而且你还动不了桌面，一动桌面就卡，点击确定之后，桌面“重启”，然后又弹出这个界面。

### 解决这个问题的方案
首先说一下，我的电脑是64位，系统是windows10，在按照以下步骤解决问题时，要结合自己的实际情况，除此之外，这个方案解决的是runtime Error中的C:\Windows\Explorer.EXE问题，对于runtime Error的其它问题我不确定是否适用，因此请谨慎尝试。
>* 首先到windows的官网下载[Autoruns](http://technet.microsoft.com/en-us/sysinternals/bb963902.aspx)。
>* 解压该文件，到文件夹里，以管理员的身份运行`Autoruns.exe`，然后会出现以下的图：<br>
![image](https://github.com/Lihit/Lihit.github.io/blob/master/assets/img/2017-10-06-solve-runtime-error-of-windows/2014-08-17_21-28-34-300x228.png)
>* 在上图中，先点击步骤1(红色圆圈)`Explorer`,然后等到红色圆圈2变成`ready`。
>* 然后将列表里所有文件的复选框**全部取消**，点击关闭，**不用保存**。
>* 接着按`CTRL + SHIFT + ESC `组合键，打开任务管理器，然后选择进程里的`windows 资源管理器`，右键选择`关闭该进程`。如下图：<br>
![image](https://github.com/Lihit/Lihit.github.io/blob/master/assets/img/2017-10-06-solve-runtime-error-of-windows/2014-08-17_21-33-51-300x132.png)
>* 此时电脑的桌面应该是变黑了，然后在打开的任务管理器（上图），点击`文件`，选择`运行新任务`，输入`Explorer.exe`，点击ok即可，如下图：<br>
![image](https://github.com/Lihit/Lihit.github.io/blob/master/assets/img/2017-10-06-solve-runtime-error-of-windows/2014-08-17_21-36-22-300x165.png)
>* 然后问题应该就可以解决了，希望可以帮助到你～