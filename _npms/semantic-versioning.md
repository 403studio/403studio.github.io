---
id: semantic-versioning
title: 13-语义版本和npm
prev: publishing-npm-packages
next: scoped-packages
---

语义版本Semantic versioning(Semver)对很多项目来说是一个版本发布标准，它用一个标准的方式来显示在这次发布中做了哪种类型的修改。显示哪种类型做了修改是非常重要的，因为有时候会损害这个包的相关依赖文件的代码。

## Semver for publisher

当一个项目将要被发布与其他开发者共同分享的时候，它的起始版本号应该是1.0.1，尽管在npm上有的项目没有遵守这个原则。

之后修改发布应该按照下面的原则：
* Bug修改以及一些小的改动：使用Patch发布，增加版本号的最后一位数字，例如1.0.1
* 不损害现在功能的情况下增加新的功能：使用Minor发布，增加版本号的中间位数字，例如1.1.0
* 无法回滚或者说无法向后兼容的修改：使用Major发布，增加版本号的第一位数字，例如2.0.0

## Semver for consumers

作为一个使用者，你可以在package.json文件中指定哪类更新你的项目是可以接受的。

如果正在使用一个开始于1.0.4版本的包，下面展示了如何指定范围：
* Patch releases: 1.0 or 1.0.x or ~1.0.4
* Minor releases: 1 or 1.x or ^1.0.4
* Major releases: * or x

你也可以通过访问[Semver](https://docs.npmjs.com/misc/semver)了解更多信息。