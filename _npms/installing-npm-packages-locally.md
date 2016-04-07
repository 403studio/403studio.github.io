---
id: installing-npm-packages-locally
title: 04-本地安装npm包
prev: fixing-npm-permissions
next: using-a-package.json
---

npm包有本地安装（locally）和全局安装（globally）两种方式。如何选择安装方式取决于你想怎么使用这个包。

如果你想要自己的模块（例如Node.js' require）使用这个包，那么建议以本地locally的方式安装，同时locally也是npm包的默认安装方式。如果你想像使用命令行界面一样使用这个包（例如grunt CLI），那么建议globally的方式安装。

如果需要了解命令行界面的安装方式，可以通过[CLI doc page](https://docs.npmjs.com/cli/install)了解。

##安装

一个包可以通过命令进行下载安装
`npm install <package_name>`

通过这个命令会在当前工作目录下新建一个名为*node_modules*的目录（如果这个目录并不存在的话），我们的包也将下载到这个目录里。

**测试**

为了确定npm包被正确的安装，可以通过查看*node_modules*是否存在并且包是否已经下载。在Unix系统可以通过*ls*命令来查看，Windows系统则可以通过*dir node_modules*查看

**实例**

以lodash为例
```
npm install lodash
ls node_modules                          #use 'dir',如果是Windows系统
```
## 如果知道包的哪个版本被安装？

如果在目录下面没有package.json文件，那么包的最新版本被安装。如果有package.json，那么符合package.json里[semver rule](https://docs.npmjs.com/getting-started/semantic-versioning)分发原则的版本包被安装

## 使用安装包

当package包被安装到*node_modules*，我们就能够在代码中使用它。例如，你正在创建一个 Node.js module，你就能包含它。
```
// index.js
var lodash = require('lodash');
var output = lodash.without([1, 2, 3], 1);
console.log(output);
```
通过`node index.js`来运行此代码。显示结果将会是[2, 3]

当然如果lodash包没有被正确的安装，那么你将收到下面的错误提示：
```
module.js:340
       throw err;
Error: Cannot find module 'lodash'
```
可以在index.js所在的目录运行`npm install lodash`来解决上面遇到的问题