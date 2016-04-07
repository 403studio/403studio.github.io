---
id: fixing-npm-permissions
title: 03-npm权限修复
prev: installing-node
next: installing-npm-packages-locally
---

当试图安装一个全局包的时候你可能会遇到 EACCES 错误。这个错误表明你没有当前npm用来存储全局包命令目录的写权限。

可以通过下面两种方式之一来修复解决这个问题：

1. 修改npm默认目录的权限
2. 修改npm默认目录的位置

在做接下来修改前最好先备份您的电脑

## 方式一：修改npm默认目录的权限

1. 找到npm目录路径
`npm config get prefix`

大多数系统，目录一般是 /usr/local

**警告：**如果路径显示的是 /usr，直接采用第二种方式

2. 修改npm目录的拥有者为当前用户
`sudo chown -R $(whoami) $(npm config get prefix)/{lib/node_modules,bin,share}`

使用这个命令同时修改了npm下面子目录和其他工具命令（lib/node_modules,bin,and share）

## 方式二：修改npm默认目录的位置

有时候并不希望修改npm默认目录的拥有者，因为这样可能会导致一些其他不可预期的问题，例如：你正在与其他用户共享同一个系统

我们可以采用修改npm目录位置。在我们的案例中，使用的是用户根目录下面的隐藏目录

1. 创建一个目录用于全局包安装
`mkdir ~/.npm-global`
2. 配置npm使其使用新的目录
`npm config set prefix '~/.npm-global`
3. 打开或者新建~/.profile文件，并添加目录路径
`export PATH=~/.npm-global/bin:$PATH`
4. 返回命令行界面，更新系统变量
`source ~/.profile`

测试：不使用sudo下载一个全局包
`npm install -g jshint`jia'r

你也可以通过修改ENV环境变量来代替2~4步骤（假如你不想修改~/.profile）
`NPM_CONFIG_PREFIX=~/.npm-global npm install -g jshint`