---
id: using-tags
title: 15-使用tags标签
prev: scoped-packages
next: 
---

## 使用dist-tags

Tags是对[semver](http://semver.org/)的一种补充，用来组织和标记不同版本的包。为了增加可读性，tags能够使创建者更有效的发布他们包。

## 添加tags

为特定版本的包添加一个tag，可以使用*npm dist-tag add <pkg>@<version> [<tag>]*。访问[the CLI docs](https://docs.npmjs.com/cli/dist-tag)获取更多信息。

## 发布的时候使用tags

默认情况下，当你进行发布的时候npm会用**latest**这个tag来标记你的包。如果需要指定其他的tag可以使用使用--tag参数。例如，下面的将使用beta这个tag发布包

`npm publish --tag beta`

## 安装的时候使用tags

与发布类似，*npm install <pkg>*默认使用**latest**这个tag。你也可以使用*npm install <pkg>@<tag>*替代默认的行为。下面的案例将使用被标记为beta的版本somepkg包进行安装
`npm install somepkg@beta`

## 说明

Because dist-tags share the same namespace with semver, avoid using any tag names that may cause a conflict. The best practice is to avoid using tags beginning with a number or the letter "v".