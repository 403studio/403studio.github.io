---
id: installing-node
title: 02-安装Node.js，更新npm
prev: what-is-npm
next: fixing-npm-permissions
---

# Getting Started

{:toc}

## 安装Node.js

如果你使用的是OS X或者Windows，最好的安装方式是使用[nodejs.org](https://nodejs.org)官网提供的安装程序。如果你使用的Linux，可以通过安装程序安装，也可以通过[NodeSource's binary distributions](https://github.com/nodesource/distributions)查找合适的版本来进行安装

测试：运行 node -v。显示的版本应该高于v0.10.32

## 更新

nNode安装的时候自带了npm。然而npm要比Node更新更为频繁，因此你需要更新npm到最新的版本

`sudo npm install npm -g`

测试：运行 npm -v。显示的版本应该高于2.1.8

## 手动安装npm

对于一些有更高需求的开发者，npm模块可以通过下面地址下载
`https://registry.npmjs.org/npm/-/npm-{VERSION}.tgz`
