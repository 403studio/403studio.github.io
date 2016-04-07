---
id: using-a-package.json
title: 05-使用package.json
prev: installing-npm-packages-locally
next: updating-local-packages
---
管理本地locally npm包最好的方式是创建package.json文件

package.json文件提供很多使用的功能：

1. 它就像文档一样提供项目所依赖的包的相关信息
2. 遵循语义版本规则使用package.json我们的项目能够使用指定版本的包
3. 能够很好的与其他开发者分享代码

## 必备

一个最基本的package.json必须包含：
* "name"
 * 全部小写
 * 没有空格
 * 可以使用划线和点号
* "version"

例如：
```
{
    "name": "my-awesome-package",
    "version": "1.0.0"
}
```

## 创建一个package.json文件

我们可以通过命令来创建package.json文件
`npm init`

这个命令会在当前工作目录下面初始化一个带提问的命令行界面用以创建package.json

## --yes 标志

通常情况下带提问的命令行界面并不适合于所有人，即使你对package.json非常熟悉也希望初始化的过程简单便捷

我们可以在运行*npm init*通过添加--yes 或者 -y 来直接创建默认的package.json文件
`npm init --yes`

这个命令仅仅会提供一个问题，就是文件的作者。否则它会填写一个默认的值
```
> npm init --yes
Wrote to /home/ag_dubs/my_package/package.json:
 
{
  "name": "my_package",
  "version": "1.0.0",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [],
  "author": "ag_dubs",
  "license": "ISC",
  "repository": {
    "type": "git",
    "url": "https://github.com/ashleygwilliams/my_package.git"
  },
  "bugs": {
    "url": "https://github.com/ashleygwilliams/my_package/issues"
  },
  "homepage": "https://github.com/ashleygwilliams/my_package"
}
```

* name: 如果不是git仓库的话默认是作者的名字，git仓库则是仓库的名字
* version: 通常是1.0.0
* main: 通常是index.js
* scripts: 默认会创建一个 test 空文件脚本
* keywords: 空
* author: 命令行界面的时候你提供的名字
* license: ISC
* repository: 如果有的话是当前目录的信息
* bugs: 如果有的话是当前目录的信息
* homepage: 如果有的话是当前目录的信息

你也可以在初始化命令的时候设置一些可选的配置信息，几个有用的例如：
```
> npm set init.author.email "wombat@npmjs.com"
> npm set init.author.name "ag_dubs"
> npm set init.license "MIT"
```

**注意**
如果在package.json文件里面没有description字段的话，npm将使用README.me或者README文件的第一行替代。description信息可以帮助别人在npm上查找你的包，所以在package.json填写description信息对查找你的包是非常有用的

## 包依赖

在package.json中需要列举你的项目所依赖的包。有两种类型的包可以列举
* "dependencies": 这些包在你应用的生产环境将被包含
* "devDependencies": 这些包将只在开发和测试环境里被包含

## 手动编辑package.json

也可以手动的编辑package.json。在接下来的案例中你将创建一个包含dependencies元素的package对象。

如果仅仅只在本地开发环境下使用包依赖，那么如同上文所说可以使用devDependencies元素

例如：下面的项目将在生产环境使用任何满足major版本为1的my_dep包，同时在开发环境下使用任何满足major版本为3的my_test_framework包
```
{
  "name": "my_package",
  "version": "1.0.0",
  "dependencies": {
    "my_dep": "^1.0.0"
  },
  "devDependencies" : {
    "my_test_framework": "^3.1.0"
  }
}
```

## --save和--save-dev安装标签

将依赖包添加到package.json更简单方式是在*npm install*的时候使用--save 或者 --save-dev标签。具体用哪个标签则取决于怎么使用依赖包。

添加一条记录到package.json的dependencies元素
`npm install <package_name> --save`

添加一条记录到package.json的devDependencies元素
`npm install <package_name> --save-dev`

## 管理依赖包的版本

npm使用语义版本（或者通常所说的SemVer）来管理包的版本以及包的版本范围

如果在你的目录下面有package.json文件，当你运行*npm install*，npm将查找package.json文件的依赖包信息下载符合SemVer规则的最新版本的包