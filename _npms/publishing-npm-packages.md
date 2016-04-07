---
id: publishing-npm-packages
title: 12-发布npm包
prev: creating-node-modules
next: semantic-versioning
---

你可以发布任何包含了package.json文件的目录，例如[node module](/npm/creating-node-modules)。

## 创建用户

首先你必须在npm registry拥有一个用户才能够进行发布。如果还没有用户，可以通过*npm adduser*进行创建。如果你通过网站创建了一个用户，可以通过*npm login*在本地客户端存储用户凭证。
 
测试：使用*npm config ls*来确定在你的本地客户端用户凭证已经被存储了。可以在[https://npmjs.com/~](https://npmjs.com/~)检查凭证已经添加到registry

## 发布包

使用*npm publish*来发布包。

目录下的所有文件在发布的时候都将被包含进去除非在本地.gitignore或.npmignore文件里指定了被排除在外。你可以通过访问[https://docs.npmjs.com/misc/developers](https://docs.npmjs.com/misc/developers)来了解.gitignore和.npmignore文件的相关信息。

## 更新包

当你对包做出修改的时候，可以通过使用*npm version <update_type>*对包进行更新，update_type是语义版本发布类型：patch，minor，major三个之一。如果你的包有git repository的话同时也会添加一个标签伴随着发布版本号。

更新发布版本号之后，需要再次发布 *npm publish*。

访问https://npmjs.com/package/<package>，你会发现包的版本号已经被更新了。

网站上的REAMME文件在没有新的包版本发布前是不会更新的，所以为了解决这个文档显示问题你需要运行*npm version patch*和*npm publish*命令。