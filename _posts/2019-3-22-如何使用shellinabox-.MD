---
layout:     post
title:      Web终端之使用shellinabox在浏览器进行登录
subtitle:   linux下利用Ngrok在外网登录终端
date:       2019-3-22
author:     k
header-img: img/post-bg-re-vs-ng2.jpg
catalog: true
tags:
    - Blog
---

> 走先人的路，后人少走路。

# 前言 大侠请留步

1.我用的是kali2.0 好了我们开始吧！
首先在kali里下载shellinabox
   get install shellinabox
   
![](https://s2.ax1x.com/2019/03/22/A8LVG4.png)

2.安装好了以后就可以启动了，在这里我们可以通过命令在后台运行

   shellinaboxd -b -t
   
     -b 在后台运行
     -t 使用基于HTTP协议的终端
     
![](https://s2.ax1x.com/2019/03/22/A8LZRJ.md.png)

3.接下来我们可以在本地浏览器先访问一下，这里我访问的是我的kali IP地址

![](https://s2.ax1x.com/2019/03/22/A8LnMR.png)

4.然后使用免费的Ngrok映射到公网，注意这里的本地端口需要修改成kali的IP和端口

![](https://s2.ax1x.com/2019/03/22/A8Lez9.png)

5.出现下图的界面，那恭喜你已经成功了

![](https://s2.ax1x.com/2019/03/22/A8Lus1.png)

6. 最后使用Ngrok映射出的公网在浏览器登录就可以了，当出现下面的界面就Ok了

![](https://s2.ax1x.com/2019/03/22/A8LEiF.png)


 最后的最后小小的说一下，其实我也是个小白中的小白，好笑的是我也才学习没有一个月了，在这里就是想说一下希望有和我一样的人我们可以一起进步。    
