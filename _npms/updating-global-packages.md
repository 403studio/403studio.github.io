---
id: updating-global-packages
title: 09-更新全局globally包
prev: installing-npm-packages-globally
next: uninstalling-global-packages
---

全部包可以通过命令*npm install-g <package>*进行更新
`npm install -g jshint`

你可以通过*npm outdated -g --depth=0*来查看哪些全局包需要被更新

可以使用*npm updated -g*对所有的全局包进行更新。然而在低于2.6.1的版本，这个命令被认为是更新所有过期版本的包。