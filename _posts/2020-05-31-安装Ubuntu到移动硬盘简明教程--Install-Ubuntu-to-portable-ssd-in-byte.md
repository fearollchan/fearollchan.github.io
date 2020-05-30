---
layout:     post
title:      安装Ubuntu到移动硬盘简明教程 | Install Ubuntu to portable ssd in byte
subtitle:   
date:       2020-05-31
author:     Moon
header-img: img/post-bg-github-cup.jpg
catalog: true
tags:
    - Linux
    - Ubuntu
---
>记录首次安装Ubuntu to go, 看了网上一些文章感觉内容太多（细节），想简化一下懒人安装，可能细节不到位，有问题欢迎指出！

# 准备
#### 硬件
* windows laptop
* U盘，（需要格式化，请提前备份资料）
* 移动硬盘
#### 软件
* Linux 发行版的镜像文件(*.iso ，官网，国内镜像托管均可下载)
* balenaEtcher (制作Linxu启动引导U盘)
# 开始
#### 制作引导U盘
	打开balenaEtcher软件，选择*.iso烧录到指定的U盘。
#### 删除移动硬盘的数据卷
	插入移动硬盘后，打开windows系统的磁盘管理，删除该移动硬盘的数据卷，使硬盘容量变为未分配状态。
#### 安装
	关闭电脑后，插入启动盘和移动硬盘，重新开机，进入BIOS选项，选择启动盘启动。
	之后进入Ubuntu的安装，在安装类型选择 其他选项,自己进行分区。
##### 对于分区
	Linxu系统为目录结构，分区根据自己的使用需求，设置不同的大小。
	![文件系统与挂载](img/post_install_ubuntu.png)
	通常设置4个分区，/ ，/home, swap,/boot。在日常使用中我比较倾向于使用/usr目录，所以我会给根目录更多的空间（非挂载点的使用的是根目录/的空间）。
	以120g的portale ssd为例,在安装类型的设备中, 找到移动硬盘对应的设备，点击左下角的“+”加号，分配分区大小，type,以及挂载点。
|分区|大小|备注|
|:--:|:--:|:---:|
|/boot|500M  |type选择efi filesystem  |
|/  |50G  |type: ext4  |
|/home  |50G |type: ext4  |
|SWAP |8G |type: swap。物理内存8G，4~16G其SWAP分区大于等于8G[1]。 |
|未分配 |Rest |备用 |
#### 等待安装
# 后记
	安装后，启动顺序首先是Linux，若没插入移动硬盘会进入grub模式，输入exit退出进入windows。可以修改uefi的boot order进行启动优先的设置。
# 参考资料
[1]	tutorial：https://blog.csdn.net/ctthuangcheng/article/details/50356638
[2]  tutorial：https://www.cnblogs.com/wtc87/p/12153024.html
[3]  分区背景知识：https://wizardforcel.gitbooks.io/vbird-linux-basic-4e/content/20.html