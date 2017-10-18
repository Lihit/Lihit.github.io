---
layout: post
title: 解决ubuntu下sublime text中文输入问题
date: 2017-10-06
tags:
- 系统问题
- sublime
categories: 
- ubuntu 
description: 在linux下，sublime text对中文输入并不是很友好，一般不能直接输入中文。
---

## 关于sublime和中文输入
sublime text是一个写代码的神器，其强大的插件功能和代码高亮成为了我写代码的首选，而且只要进行一些设置，它还可以作为C++和python的轻量级的编译器，但是在ubuntu下，sublime并不能直接输入中文，这给我造成了极大的困扰，因为平时还是要经常写中文的，比如写代码注释或是我现在用中文写这篇博客等。因此打算解决这个问题，网上搜了很多方案，很乱而且大多都是不成功，下面写一下实验成功的并且比较简单的解决方案。

## 解决方案
这个方案是[lyfeyaj](https://github.com/lyfeyaj)解决的，叫[sublime-text-imfix](https://github.com/lyfeyaj/sublime-text-imfix)
### 运行环境
* ubuntu 14.04
* sublime text3

### 步骤
* 将更新和升级你的linux系统，这样可以防止出现其它问题.<br>
`sudo apt-get update && sudo apt-get upgrade`
* 先把上述的项目clone到本地.<br>
`git clone https://github.com/lyfeyaj/sublime-text-imfix.git`
* 打开终端，运行`cd sublime-text-imfix`,到这个项目中.
* 输入命令：`./sublime-imfix`脚本.
* 这样应该就大功告成了，在终端输入`subl`就可以打开sublime了.<br>
![](https://raw.githubusercontent.com/Lihit/Lihit.github.io/master/assets/img/2017-10-06-solve-runtime-error-of-windows/fcitx.png)

