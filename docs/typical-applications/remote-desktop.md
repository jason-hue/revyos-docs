---
title: 远程连接Licheepi 4A桌面
sidebar_position: 7
---

# 远程连接Licheepi 4A桌面

本文介绍多种方法远程连接到Licheepi 4A的桌面环境，帮助用户实现无需外接显示器的远程开发和使用。

## 前提条件

- Licheepi 4A开发板
- RevyOS系统
- 稳定的网络连接
- 远程主机（Windows/Linux/Mac）

前言：想使用荔枝派4A桌面，但是每次使用需要切换键盘鼠标和显示器太不方便了，而且还不能录屏，遂尝试vnc远程桌面。

### 荔枝4A需要的操作：

```bash
sudo apt-get update
//通常情况荔枝派4A官方系统桌面就是xfce4
sudo apt-get install xfce4 xfce4-goodies
```

##### 安装tigervncserver:

```bash
sudo apt install tigervnc-standalone-server
```

##### 初始化vncserver:

安装完成 VNC 服务器的初始配置后，使用 vncserver 命令设置安全密码并创建初始配置文件:

```bash
sudo vncserver
```

第一次运行，系统会提示您**设置远程访问机器的密码**

##### 编辑配置文件：

```bash
vim .vnc/xstartup
```

粘贴如下代码并保存：

```bash
#!/bin/sh
unset SESSION_MANAGER
unset DBUS_SESSION_BUS_ADDRESS
startxfce4 &
```

##### 启动VNC服务：

```bash
sudo vncserver -localhost no :1
```

注：不添加选项会导致荔枝派4A vncserver之监测本地回环的5901端口而不是所有的5901.(我就是在这被搞了，一直远程不上，突发奇想在荔枝派上访问自己的VNC才发现问题。)

检查监听状态：

```bash
sudo netstat -tuln | grep 5901
```

附：

```bash
# 查看vncserver服务
sudo vncserver -list
# kill 5901端口的服务
sudo vncserver -kill :1
```

### 电脑上需要的操作：

##### 安装remmina:

```bash
sudo apt install remmina remmina-plugin-vnc
```

##### 启动remmina：

`remmina`

启动UI后点击左上角加号添加配置：

![image-20240926193206009](https://raw.githubusercontent.com/jason-hue/plct/main/imagesimage-20240926193206009.png)

点击保存并连接后即可连接成功

![image-20240926193333404](https://raw.githubusercontent.com/jason-hue/plct/main/imagesimage-20240926193333404.png)

by:可以自己设置一个开机自启服务，更方便。