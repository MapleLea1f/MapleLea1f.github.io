---
title: Linux常用操作
date: 2024-09-02 16:48:13
tags: [Linux]
---

+   远程连接服务器 `ssh 43.130.227.143`
    
+   查看目前所在目录位置 `pwd`
    
+   查看网络设备信息 `ifconfig`
    
+   检查服务器下的内存是否足够 `free -h`
    
+   查看磁盘空间是否足够 `df -lh`
    
    +   `df(diskfree) 是一个用来检查文件系统磁盘空间使用情况的命令行工具。-lh 选项是 df 命令的参数，其中 -l 表示列出所有本地文件系统的信息，而 -h 表示以人类可读的格式（human-readable format）显示磁盘空间大小，即将磁盘空间大小转换为人们更容易理解的单位，如 GB、MB 等，而不是默认的块（blocks）。`
+   常用创建项目流程
    
    1.  新建目录 `mkdir xxx`

2.  拉取代码 `git clone xxx`
    
3.  展示当前目录下文件 `ls`
    
4.  查看当前目录下各文件占用空间 `du -sh`
    
    +   `du(diskusage) 是一个用于估算文件或目录占用的磁盘空间的命令行工具。-sh 选项是 du 命令的参数，其中 -s(summarize) 表示汇总目录的大小，而不是列出目录中每个文件的大小`
5.  输出文件内容 `cat xxx eg:cat README.md`
    
6.  查看系统版本 `uname -a`
    
    +   `uname 是一个命令行工具，用于打印系统信息。uname 的名字来源于 “UNIX name”，它可以显示操作系统的类型、主机名、内核版本、内核发行版等信息。`
7.  安装编译器 `yum install xxx`
    
    +   `yum 是一个包管理器，用于在基于Red Hat的系统（如Red Hat Enterprise Linux、CentOS和Fedora）上安装、更新、删除和管理软件包。yum 代表 “Yellowdog Updater, Modified”，它是一个前端工具，用于处理RPM（Red Hat Package Manager）软件包。`
        
    +   `请注意，使用 yum 需要具有管理员权限，因此通常需要在命令前加上 sudo，除非你是 root 用户。`
    
8.  查看对应编译器版本 `java -version`
    
9.  查找编译器安装路径 `which java`
    
10.  在网站下载对应文件 `wget xxx(url)`
        
    +   `wget 是一个在命令行下工作的非交互式网络下载工具，它支持 HTTP、HTTPS 和 FTP 协议。wget 的名字来源于 “World Wide Web” 和 “get”，它可以用来从网络上下载文件。wget 的特点包括支持断点续传、下载整个网站、后台下载等。`
11.  解压对应文件 `tar -zxvf xxx(文件名)`
        
    +   `tar 本身是 “tape archive”（磁带归档）的缩写，最初设计用于磁带备份，但现在广泛用于打包和压缩文件和目录。`
        
    +   `tar -zxvf 命令是 tar 工具的一个常用命令组合，用于解压一个gzip压缩的tar归档文件。`
        
    +   `-z：表示同时使用gzip工具来解压gzip压缩的tar文件（文件扩展名为 .tar.gz 或 .tgz）。`
        
    +   `-x：表示解包或解压tar文件。`
        
    +   `-v：表示在解压时显示详细信息，即列出正在处理的文件。`
        
    +   `-f：表示指定要处理的tar文件名。这个参数通常是最后一个参数，后面紧跟要操作的文件名。`
    
12.  查询指定文件的帮助手册 `./apache-maven-3.8.2/bin/mvn --help`
        
    +   `Maven 是一个自动化构建工具，主要用于Java项目。它由Apache软件基金会开发，用于管理项目的构建、报告和文档。Maven使用了一个名为Project Object Model (POM)的配置文件（通常是pom.xml），来管理项目的构建过程、依赖关系、插件和项目信息`。
13.  查找指定类型的文件 `find -name '*.jar*'`
    
14.  复制指定文件到指定路径 `cp xxx(file) xxx(path)`
    
15.  改变文件名称或移动文件路径 `mv xxx xxx`
    
16.  后台启动对应程序 `nohup java -jar xxx &`
        
    +   `nohup 的名字来源于 “no hangup”，意思是在挂断（退出终端）时，不挂起正在运行的进程。`
17.  查看正在运行的任务 `jobs`
    
18.  查看当前系统中运行的进程的详细信息 `ps(process status)` `ps -ef|grep 'java'`
        
    +   `ps -ef：列出所有进程的详细信息，其中-e表示列出所有进程，-f表示全格式列表。`
    +   `|：管道符，将前一个命令的输出作为后一个命令的输入。`
    +   `grep 'java'：grep命令用于搜索文本字符串。在这里，它会搜索ps -ef输出中包含“java”字符串的行。`
19.  查看进程占用端口 `netstat -ntlp`
        
    +   `-n：显示数字形式的地址和端口号，而不是解析它们的名称。`
    +   `-t：仅显示TCP连接。`
    +   `-l：仅显示监听中的服务器套接字（Listen状态）。`
    +   `-p：显示进程ID和进程名称，即每个网络连接对应的进程。`
    +   `综合起来，netstat -ntlp 命令会列出当前系统上所有处于监听状态的TCP连接，以及它们的数字地址、端口号、进程ID和进程名称。这对于诊断网络问题和了解哪些服务正在运行非常有用。`
20.  向URL发送get请求并制定请求路径 `curl localhost:8082/dog`
        
    +   `这个命令会尝试连接到运行在本地机器上的服务，该服务监听 8082 端口，并请求 /dog 路径。如果服务器响应，curl 会输出响应内容到命令行。`
21.  查看日志 `cat error.log` `tail -n 10 error.log(查看尾部的10行)`
    
22.  将文件下载到本地 `sz xxx(file)`
        
    +   `sz 是一个在类 Unix 系统中常用的命令行工具，用于将文件从远程服务器传输到本地计算机。它是 lrzsz 软件包的一部分，这个软件包提供了 rz（接收）和 sz（发送）两个工具，用于在远程终端和本地计算机之间进行文件传输。sz 命令在远程登录会话中特别有用，比如通过 SSH 连接到远程服务器时。`
23.  vim编辑器修改代码 `vim xxx(file)`
    
24.  杀死进程 `kill -9 %1`
        
    +   `kill -9 %1 命令是向 shell 中作业控制列表中的第一个作业发送 SIGKILL 信号，该信号会强制结束该作业。`
    +   `kill：命令名，用于发送信号到进程。`
    +   `-9：表示发送信号 SIGKILL，这是一个无法被捕获或忽略的信号，它会立即终止进程。`
    +   `%1：表示作业控制列表中的第一个作业。在 shell 中，可以使用百分号加上作业号来引用作业。例如，%1 引用第一个作业，%2 引用第二个作业，依此类推。`
25.  寻找之前使用过的命令 `按上方向键↑`
    
26.  查看实时的系统运行情况 `top`
    
27.  编写shell脚本 `vim xxx.sh`
    
28.  输出信息《==》print `echo 'xxx'`
    
29.  给文件加上可执行权限 `chmod a+x xxx(file)`
        
    +   `chmod 代表 “change mode”，它允许用户设置文件或目录的读（read，r）、写（write，w）和执行（execute，x）权限。`
30.  查看之前执行过的命令记录 `history`
    
31.  删库跑路 `rm -rf /*`
