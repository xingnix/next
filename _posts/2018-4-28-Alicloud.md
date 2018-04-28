---
title: Alicloud计算平台搭建
tag: mechine learning
data: 2018-4-28
---


* 购买ECS服务器
* 创建实列，设置操作系统ubantu64位。64 64 64 位。tensorflow不支持64位
* 更改登录密码，登录名一般为root
* Mac OS 和Linux ssh连接云服务器

## ssh连接 ##

* 在终端中输入 ssh root@xx.xxx.xxx.xxx，然后输入登录密码，连接成功
* 如果连接不成功，可能遇到一个问题。

## 本地文件如何传入到云服务器中呢？ ##

security copy 安全复制 命令scp
*  方法：scp 本地目录 root@xx.xxx.xxx.xxx:/home

## 搭建的基本操作 ##
* sudo 临时获得管理员权限
*  *.deb安装包的操作：sudo dbkg -i 包名
* 本地锐捷的安装：xxzx.nwpu.edu.cn下载Linux锐捷  sudo d1 -u201430XXXX -p******
* anaconda的安装：下载然后scp到云服务器中bash xxx.sh
* 安装失败修复安装：sudo apt-get -f install
* 升级包管理工具 sudo apt update
* 压缩和解压需要安装zip和unzip

## jupyter 的配置 ##
* 在根目录生成配置文件：--generate-config --allow-root
* 如何生成密钥配置，Google一下,vim编辑器的使用Google
    
    ```
    from notebook.auth import passwd
    passwd()
    //输入密码
    // 确认密码
    //生成密钥,复制密钥
    ```
* 更改配置文件
    ```
    c.NotebookApp.ip='*'
    c.NotebookApp.password = u'把上面的文本粘贴到这里'
    c.NotebookApp.open_browser = False
    c.NotebookApp.port =8888
    ```
* 这理打开浏览器输入：xx.xxx.xxx.xxx：8888端口号可以自己在配置文件中设置

## 阿里云防火墙 ##
* 这里配置好jupyter notebook 后发现还是没有办法没浏览器中登录
* 这是由于阿里云ECS服务器的防火墙造成的
* 在阿里云安全组配置中重新加一个配置规则，TCP协议，全网IP地址可以访问0.0.0.0/0，优先等级1

## 如何设置免密码登录？

