---
title: D-Robotics（RDKX5）
date: 2025-09-01T15:35:51Z
lastmod: 2025-09-20T13:15:37Z
---

# D-Robotics（RDKX5）

参考文档：【[https://developer.d-robotics.cc/rdk_doc/Quick_start](https://developer.d-robotics.cc/rdk_doc/Quick_start "RDK5")】

[10. 算法工具链开发指南 — 地平线RDK套件用户手册 2.0.0 文档](https://developer.d-robotics.cc/api/v1/fileData/documents_rdk/quant_toolchain_development/index.html)

---

## Linux指令

> 速查表：【[Linux 命令大全速查表 PDF - 2025 | LabEx](https://linux-commands.labex.io/zh/)】

```python
tar -cvf archive.tar folder  
gzip file  
gunzip file.gz 
zip -r archive.zip folder  
unzip archive.zip 

sudo chmod +x /etc/init.d/your_script_name
sudo systemctl enable your_script_name

关机指令
sudo shutdown -h now

sudo reboot
```

### nano使用

* Ctrl+G，显示帮助文本
* Ctrl+O，保存当前文件
* Ctrl+R，读取其他文件并插入光标位置
* Ctrl+Y，跳至上一屏幕
* Ctrl+K，剪切当前一行
* Ctrl+C，显示光标位置
* Ctrl+X，退出编辑文本
* Ctrl+J，对其当前段落（以空格为分隔符）
* Ctrl+W，搜索文本位置
* Ctrl+V，跳至下一屏幕
* Ctrl+U，粘贴文本至光标处
* Ctrl+T，运行拼写检查
* Ctrl+\_，跳转到某一行
* ALT+U，撤销
* ALT+E，重做
* ALT+Y, 语法高亮
* ALT+#，显示行号

#### 光标控制

移动光标：使用用方向键移动。

选择文字：按住鼠标左键拖动（然后就可以复制了）。

#### 复制文本

这取决于你用的是什么 SSH 软件。

Putty 要复制文本是选择要复制的文本点击鼠标左键即可。

Xshell 要复制文本则是选择要复制的文本按下 Ctrl+INSERT 键。

#### 粘贴文本

这取决于你用的是什么 SSH 软件。

Putty 要粘贴文本点击鼠标右键即可。

Xshell 要粘贴文本则是按下 Shift+INSERT 键。

#### 在 Nano 中启用语法高亮显示

Nano 的语法高亮规则通常在位于  **/usr/share/nano/**  目录中的配置文件中定义。

```powershell
ls /usr/share/nano
```

默认情况下，除非明确配置，**否则 Nano** 可能不会突出显示语法。要启用它，您需要修改 Nano 配置文件 `~/.nanorc`​，并包含您需要的语法文件。

```undefined
nano ~/.nanorc
```

添加以下行以包含所需的语法高亮显示规则：

```undefined
include /usr/share/nano/python.nanorc
include /usr/share/nano/c.nanorc
include /usr/share/nano/html.nanorc
```

### Linux设备指令

‍

```python
# uname -a               # 查看内核/操作系统/CPU信息
# head -n 1 /etc/issue   # 查看操作系统版本 
# cat /proc/cpuinfo      # 查看CPU信息
# hostname               # 查看计算机名 
# lspci -tv              # 列出所有PCI设备
# lsusb -tv              # 列出所有USB设备 
# lsmod                  # 列出加载的内核模块
# env                    # 查看环境变量
```

```python
# free -m                # 查看内存使用量和交换区使用量 
# df -h                  # 查看各分区使用情况 
# du -sh <目录名>        # 查看指定目录的大小 
# grep MemTotal /proc/meminfo   # 查看内存总量
# grep MemFree /proc/meminfo    # 查看空闲内存量
# uptime                 # 查看系统运行时间、用户数、负载 
# cat /proc/loadavg      # 查看系统负载
磁盘和分区

# mount | column -t      # 查看挂接的分区状态 
# fdisk -l               # 查看所有分区 
# swapon -s              # 查看所有交换分区
# hdparm -i /dev/hda     # 查看磁盘参数(仅适用于IDE设备) 
# dmesg | grep IDE       # 查看启动时IDE设备检测状况
```

```python
# ifconfig               # 查看所有网络接口的属性
 # iptables -L            # 查看防火墙设置 
# route -n               # 查看路由表 
# netstat -lntp          # 查看所有监听端口 
# netstat -antp          # 查看所有已经建立的连接
 # netstat -s             # 查看网络统计信息
进程

# ps -ef                 # 查看所有进程 
# top                    # 实时显示进程状态
```

```python
# w                      # 查看活动用户 
# id <用户名>            # 查看指定用户信息 
# last                   # 查看用户登录日志 
# cut -d: -f1 /etc/passwd   # 查看系统所有用户 
# cut -d: -f1 /etc/group    # 查看系统所有组 
# crontab -l             # 查看当前用户的计划任务
服务

# chkconfig --list       # 列出所有系统服务 
# chkconfig --list | grep on    # 列出所有启动的系统服务
```

**RPM**  
	在Linux 操作系统中，有一个系统软件包，它的功能类似于Windows里面的“添加/删除程序”，但是功能又比“添加/删除程序”强很多，它就是 Red Hat Package Manager(简称RPM)。此工具包最先是由Red Hat公司推出的，后来被其他Linux开发商所借用。由于它为Linux使用者省去了很多时间，所以被广泛应用于在Linux下安装、删除软件。

```python
# rpm -qa                # 查看所有安装的软件包
```

* apt-get update——在修改/etc/apt/sources.list或者/etc/apt/preferences之后运行该命令。此外您需要定期运行这一命令以确保您的软件包列表是最新的。  
  apt-get install packagename——安装一个新软件包（参见下文的aptitude）  
  apt-get remove packagename——卸载一个已安装的软件包（保留配置文件）  
  apt-get –purge remove packagename——卸载一个已安装的软件包（删除配置文件）  
  dpkg –force-all –purge packagename 有些软件很难卸载，而且还阻止了别的软件的应用，就可以用这个，不过有点冒险。  
  apt-get autoclean apt会把已装或已卸的软件都备份在硬盘上，所以如果需要空间的话，可以让这个命令来删除你已经删掉的软件  
  apt-get clean 这个命令会把安装的软件的备份也删除，不过这样不会影响软件的使用的。  
  apt-get upgrade——更新所有已安装的软件包  
  apt-get dist-upgrade——将系统升级到新版本  
  apt-cache search string——在软件包列表中搜索字符串  
  dpkg -l package-name-pattern——列出所有与模式相匹配的软件包。如果您不知道软件包的全名，您可以使用“*package-name-pattern*”。  
  aptitude——详细查看已安装或可用的软件包。与apt-get类似，aptitude可以通过命令行方式调用，但仅限于某些命令——最常见的有安装和卸载命令。由于aptitude比apt-get了解更多信息，可以说它更适合用来进行安装和卸载。  
  apt-cache showpkg pkgs——显示软件包信息。  
  apt-cache dumpavail——打印可用软件包列表。  
  apt-cache show pkgs——显示软件包记录，类似于dpkg –print-avail。  
  apt-cache pkgnames——打印软件包列表中所有软件包的名称。  
  dpkg -S file——这个文件属于哪个已安装软件包。  
  dpkg -L package——列出软件包中的所有文件。

‍

‍

‍

‍

‍

‍

‍

‍
