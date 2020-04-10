---
layout: post
title: 配置Github Pages出现的一些问题
description: 很久没有配置github pages，又从Windows转向unix，导致页面404，在此记录解决方案
category: blog
---

上篇博客配置写好后，推送到自己的仓库中，结果页面出现404，在这里记录出现问题的原因。

在macOS下，如果在本地folder中使用`jekyll serve`命令本地测试效果，会在目录下生成`.jekyll-cache`缓存文件夹。该文件夹上传至仓库后，被github pages服务端解析会出错，导致404.因此一定要删除该文件夹后再push。

删除`.jekyll-cache`后导致git push失败，原因是远程仓库中存在本地提交的不存在的文件。应当先进行merge：
```bash
git pull origin master
```
全部步骤为：
```bash
git add --all
git commit -m "commit log"
git pull origin master
git push -u origin master
```
OK. git刚入门，还需多练练手。  