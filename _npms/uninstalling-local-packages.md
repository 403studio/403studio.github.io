---
id: uninstalling-local-packages
title: 07-卸载本地locally包
prev: updating-local-packages
next: installing-npm-packages-globally
---

在你的node_modules目录下运行*npm uninstall <package>*可以删除卸载<package>包
`npm uninstall lodash`

如果同时需要将package.json的依赖关系同时删除，可以使用save 标签
`npm uninstall --save lodash`