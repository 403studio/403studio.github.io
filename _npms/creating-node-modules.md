---
id: creating-node-modules
title: 11-创建Node.js模块
prev: uninstalling-global-packages
next: publishing-npm-packages
---

Node.js模块是能够发布到npm的一类包。当你创建一个新的模块的时候，首先是创建一个package.json文件。

可以通过*npm init*来创建package.json。它会提示输入一些package.json字段值。两个必填字段是name和version。如果你想要对一些主要部分设定值，可以在index.js文件使用default字段。

如果你想要对author字段增加一些信息，可以使用下面的格式（email和网站地址都是选填的）
`Your Name <email@example.com>` (http://example.com)

当package.json文件创建以后，你就可以创建模块被包含时自动加载的文件，默认情况是index.js

在index.js文件里，添加一个作为exports对象属性的函数，那么这个函数就可以在其他代码中使用
```
exports.printMsg = function() {
  console.log("This is a message from the demo package");
}
```

测试：
1. 发布你的包到npm
2. 在你的项目外新建一个目录，使用命令行进入这个目录
3. 运行*npm install <package>*
4. 创建一个包含package并且调用printMsg方法的文件test.js
5. 运行*node test.js*。消息将被打印显示出来