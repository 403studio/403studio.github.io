---
id: installing-npm-packages-globally
title: 08-安装全局globally包
prev: uninstalling-local-packages
next: updating-global-packages
---

有两种安装npm包的方式：本地（lcoally）和全局（globally）。选择哪种安装方式取决于你怎么使用这些包。

如果你想要像命令行工具一样使用这些包，例如grunt CLI，那么你可以使用全局globally的安装方式。另外，如果你只是需要在自己的模块来使用这些包，例如Node's require，那么你可以使用本地locally的安装方式。

可以使用一个简单的命令来下载全局包*npm install -g <package>*，例如
`sudo npm install -g jshint`