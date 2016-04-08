---
id: packages
title: 01-包以及模块
prev: using-tags
---

Node'js和npm对包package以及模块module有明确的定义 ，有时候我们很容易混淆二者的区别。

* package是一个包含了package.json的文件或目录。它有多样的组织形式，可以查看下文的“什么是package”了解详情
* module是任何能够被node.js' require()的文件或目录。同样它也有多种配置形式，查看下问了解详情

## 什么是package

package可以是下面的任一一种
* a) 一个被package.json文件描述的程序目录
* b) 包含a的压缩包
* c) 链接到b的url
* d) 链接到registry代码库里的 <name>@<version>文件
* e) 指向d的<name>@<tag>
* f) 满足条件e的 默认最新版本的<name>
* g) a的git url

## 什么是module

module是任何能够被node.js' require()的文件或目录。下面列举的是所有能够以module形式加载的情况
* 一个包含package.json文件的目录，package.json必须包含main字段
* 一个包含index.js文件的目录
* 一个javascript文件

## 大多数的package是module

通常情况下，npm的package在Node'js程序里面是以require形式加载的，因此很多package也可以说是module。然而并不是说package就得是module

有些package，例如CLI package只包含了命令行界面下执行的东西，并没有提供在Node'js程序下执行的main字段。这些package就不是module。

在Node程序里，module也可以是一个被加载的文件，例如`var req = require('request')`， 我们能够说“req是一个request模块”

