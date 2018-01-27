---
layout: post
title: CentOS常用命令
permalink: CentosCommand.html
description: 系统
date: 2018-01-26 14:09:07 +08:00
tags: [Linux,命令]
---
### 网络
1. 查看ip信息 `$ ip addr`/`ifconfig`，
2. 若网络未连接，则 `$ cd /etc/sysconfig/network-scripts/`，
3. 使用`ls`命令查看，以`ifcfg-ens`开头的文件，并进行编辑，如`# vi ifcfg-ens33 `，
4. 将'`ONBOOT`值改为`yes`，保存退出，即系统启动时自动激活网卡。

### 防火墙
- `firewall-cmd --query-port=6379/tcp` 命令，检测端口是否开启，如果返回结果为no，那么证明6379端口没有开启。
- `firewall-cmd --add-port=6379/tcp` 命令，则是将6379端口开启，返回success。（`--permanent` 参数代表永久生效，没有此参数重启后失效）。

### 端口
- 查看端口 `netstat –apn | grep 8080`

### tar压缩命令

　#### 主选项

　　`c` 创建一个新的Tar文件，即压缩文件。
　　    $ tar cf filename.tar file1 file2 ...
　　    $ tar cf filename.tar ./*  

　　`x` 从Tar文件中释放文件，即解压文件。
　　    $ tar xf filename.tar 

　　`t` 列出Tar文件的内容。
　　    $ tar tf filename.tar

 > 注意: c、x、t 仅能同时使用一个。
 
　#### 辅助选项
    
　　`f` filename，后面紧跟文档名，通常必有此参数。
    
　　`z` 是否需要用 gzip 压缩或解压， 一般格式为`xx.tar.gz`或`xx. tgz`。
　　    $ tar czf test.tar.gz a b 压缩
　　    $ tar xzf test.tar.gz a b 解压

　　`j` 是否需要用 bzip2 压缩或解压，一般格式为`xx.tar.bz2`。
    
　　`v` 压缩过程中显示文件信息（常用） 
    
　　`--exclude FILE`：在压缩的过程中， 排除`FILE`文件
    
　#### 总结

　　打包 `$ tar cvf f.tar f`
    
　　压缩 `$ tar czvf f.tgz`
    
　　释放 `$ tar xvf f.tar f`
    
　　解压 `$ tar xzvf f.tgz`
    
　　查看 `$ tar tf f.tar`
    
### 组件安装

　#### telent
　> windows系统可在`组件`中安装

　　检测是否存在
     
　　    $ rpm -qa| grep telnet
      
　　安装

　　    $ yum -y install telnet

　#### wget
　> wget是一个下载文件的工具，用来从指定的URL下载文件。
     
　　安装

　　    $ yum -y install wget
　　使用

　　    $ wget url

　#### mosh
　　> [Mosh](https://mosh.org/)是一个移动Shell，可用于SSH连接（远程登陆），具有响应快、支持间歇性连接等优点，使用时需要在服务器端与客户端上分别安装。

　　安装

　　    $ yum -y install epel-release
　　    $ yum makecache
　　    $ yum -y install mosh
      
　　启动

　　    $ mosh-server
