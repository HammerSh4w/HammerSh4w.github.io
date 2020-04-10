---
layout: post
title: Terminal代理配置
description: shadowsocks会自动修改macos Terminal代理，本篇总结了代理配置方法
category: blog
---

好久不见。这篇博客算是一个重启，之后的学习笔记基本上都会在这里发布。Markdown并不难，而且搭配VSCode非常易用。

## Terminal代理配置
为了翻GFW，我们使用Shadowsocks翻墙，在MacOS中，Shadowsocks会自动修改系统中proxy配置。但自动更改的配置存在一些问题，在这里我们将讨论一下这个问题。

## 默认情况的代理配置
打开Terminal，查看当前proxy，输入：  
```shell
env|grep -I proxy
```  
回显：  
```shell
http_proxy=http://127.0.0.1:1087  
https_proxy=http://127.0.0.1:1087
```
  
但shadowsocks中的http代理配置指定端口为`12688`，所以在默认配置下，像brew等命令将无法联网，会提示`Failed to connect to 127.0.0.1 port 1087`错误。需要修改系统代理配置。

## 修改代理配置
在Terminal中设置：
HTTP代理：
```shell
export http_proxy="http://127.0.0.1:12688"
```
HTTPS代理：
```shell
export https_proxy="http://127.0.0.1:12688"
```
可用curl进行测试：
```shell
curl http://www.google.com
curl https://www.google.com
```

## 取消代理配置
Terminal中输入
```shell
unset http_proxy
unset https_proxy
```

## 在bash_profile中配置函数
编辑`/Users/you/.bash_profile`，加入设置
```bash
function proxy_off(){
    unset http_proxy
    unset https_proxy
    echo -e "已关闭代理"
}
function proxy_on() {
    export no_proxy="localhost,127.0.0.1,localaddress,.localdomain.com"
    export http_proxy="http://127.0.0.1:12688"
    export https_proxy=$http_proxy
    echo -e "已开启代理"
}
```
之后终端中source一下
```shell
source .bash_profile
```
开启代理
```shell
proxy_on
```
关闭代理
```shell
proxy_off
```

MacOS的Terminal代理会被Shadowsocks的pac自动配置。不知在Shadowsocks软件中是否可以设置自动代理配置的端口号。