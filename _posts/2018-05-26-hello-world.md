---
layout: post
title: Hello World!
description: GitHub Pages博客的第一篇，关于这个博客做一个简单说明。
category: blog
---

## 关于这个博客

此博客是HammerSh4w的学习笔记，将伴随HammerSh4w之后若干年的学术旅途。`Happy Coding！`

## 语言

所有文章将通过`Markdown`标记语言完成，Markdown的优点包括：

* 简单
* 编写过程可完全脱离鼠标
* 完备的社区支持



## 编辑器

~~Typora~~

> 说明：Typora编辑器渲染的界面与github pages的jekyll渲染差距较大，故弃用

`Sublime`

> Sublime大法好


## 模版

博客模版来自：[https://github.com/beiyuu/Github-Pages-Example](https://github.com/beiyuu/Github-Pages-Example)

在此基础上做了一些修改。



## 笔记：Github Pages + Jekyll


##### 步骤1：Github Pages: [链接](https://pages.github.com/) 


  * 遇到的问题：仓库建立后，若浏览器访问出现404，或许打开`仓库username.github.io-Settings`看到

     > Your site is published at https://*username*.github.io/

     这时再访问就应该OK了。

##### 步骤2：安装Ruby


##### 步骤3：安装Gem


##### 步骤4：~~gem install jekyll~~


  > 不要使用gem安装的版本，应使用与github pages一致的版本，参考吐槽

##### 步骤5：套用博客模版并进行修改


  * 把模版git到项目目录下，在项目目录下打开terminal，输入
     `jekyll serve`
     即可在本地`127.0.0.1:4000`运行调试。

  * 对模版进行调整

     - jekyll会根据根目录下的`index.md`或其他格式的index文件在`_site`文件夹下生成实际的页面，所以对主页的调整在`index.md`中完成

     - 针对页面左侧的图片，即`aside`类，修改`_include/styl2.css`，找到`.index-wrapper .aside`并完成如下修改

       ``` javascript
       .index-wrapper .aside {
         position: fixed;
         top: 0;
         left: 0;
         width: 30%;
         height: 100%;
         max-width: 500px;
         background-image:url(../images/background2.jpg);
       }
       ```

       此外，`info-card`类的文字位置在如下的`margin-top`中设定

       ``` javascript
       .index-wrapper .info-card {
         position: absolute;
         margin-top: 8%;
         text-align: center;
         width: 100%;
       }
       ```

     - 因对前端技术不熟悉，经过摸索修改好了css，故在此记录

     - 删除了原模版中的评论，和微博展示模块

     - 目前整个博客的前端十分简陋，以后有时间再折腾

##### 步骤6：最后git

  bash如下

   ``` bash
   git add --all
   git commit -m "whatever you need"
   git push
   ```

## 吐槽

为了和Github Pages使用的jekyll保持一致，这样可以保证本地渲染的效果与Pages相同，我们后来又使用

[https://help.github.com/articles/setting-up-your-github-pages-site-locally-with-jekyll/](https://help.github.com/articles/setting-up-your-github-pages-site-locally-with-jekyll/)

学习建站过程，中间的坑比较多，有如下几个问题应注意：

  + ruby应安装完整，包括msys，否则后续模块会报错

  + Step1与Step3的路径设置并没有看懂，会出现repo里再repo，这样我不知道Pages能否自动识别index，因此只按照他的步骤进行`bundle install`安装jekyll，之后自行发挥

  + 没接触过前端和web，搞起来很蛋疼，而且ruby windows真的是服气。~~谁让你用windows的~~

  + 发现Github Pages支持的Markdown语法有限，比如加粗，斜体都不能支持，而且缩进效果并不理想