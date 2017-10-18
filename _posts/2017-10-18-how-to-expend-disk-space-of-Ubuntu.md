---
layout: post
title: 扩展虚拟机Ubuntu的磁盘容量
date: 2017-10-18
tags:
- 系统
categories: 
- ubuntu
description: 关于如何解决在虚拟机下，给Ubuntu系统扩展磁盘容量的问题。
---

## 关于这个问题
我们在安装虚拟机的时候，一开始系统的磁盘容量是固定的，但是如果一开始分配的空间不够大，随着我们在虚拟机系统上创建的文件越来越多，就有可能造成磁盘空间不足，而且是由于是虚拟机下linux系统，肯定不能像我们在windows下直接到磁盘管理设置扩展磁盘容量，但我们肯定不想因为这个问题重新装这个系统，因此下面给出解决这个问题的解决方法。

## 实验环境
* 虚拟机软件`VMware Workstation Pro`.
* 虚拟机中装的是`Ubuntu14.04`.
* 主机是`Win7`.

##　解决方案
* 点击`VMware Workstation Pro`这个软件菜单栏的`虚拟机`，再选择`设置`，如下图：<br>
![](https://raw.githubusercontent.com/Lihit/Lihit.github.io/master/assets/img/2017-10-18-how-to-expend-disk-space-of-Ubuntu/p1.PNG)
* 点击`硬盘(SCSI)`,再点击`扩展`，将容量调成合适的大小，点击确定
* 然后打开这个Ubuntu系统，安装`gparted`,安装需要联网，因此确保你连着网，安装步骤如下：
    * 打开终端，输入`sudo apt-get update` 更新你的系统软件
    * 再`sudo apt-get install gparted `
* 安装完之后打开这个软件`sudo gparted`，如下图：<br>
![](https://raw.githubusercontent.com/Lihit/Lihit.github.io/master/assets/img/2017-10-18-how-to-expend-disk-space-of-Ubuntu/p2.png)
*　**这一步要视情况而定**　从上图可以看到我的主分区是`/dev/sda1`,但是刚分配的磁盘是`unallocated`,他是跟在`/dev/sd2`后面的，需要注意的是要扩展的分区要相邻，因此我这里是不能直接对｀sd1｀进行扩展的，如果你要扩展的分区后面直接连着刚分配的磁盘空间，可以忽略这一步。因此需要将`/dev/sda2`和其下边的`/dev/sda5`删除，**在删除之前建议先备份**。具体步骤如下：
    * 右键`/dev/sda5`,选择`swapoff`
    * 再右键`/dev/sda5`选择`delete`
    * 接着右键`/dev/sda2`选择`delete`
    * 然后就可以看到现在只剩下`/dev/sda1`和`unallocated`。
![](https://raw.githubusercontent.com/Lihit/Lihit.github.io/master/assets/img/2017-10-18-how-to-expend-disk-space-of-Ubuntu/p3.png)
* 接着右键`/dev/sda1`，选择`resize/move`<br>
![](https://raw.githubusercontent.com/Lihit/Lihit.github.io/master/assets/img/2017-10-18-how-to-expend-disk-space-of-Ubuntu/p4.png)
* 将上图中，上边的那个黑色箭头，拉到最右边，或是你也可以直接输入要扩展的容量，再点击`resize`
* 最后点击绿色的√，会弹出一个对话框，再点击`apply`即可。如下图:<br>
![](https://raw.githubusercontent.com/Lihit/Lihit.github.io/master/assets/img/2017-10-18-how-to-expend-disk-space-of-Ubuntu/p5.png)