---
id: scoped-packages
title: 14-使用scoped packages
prev: semantic-versioning
next: using-tags
---

Scopes在npm模块里就像是命名空间一样。如果一个包的名字以@符号开始，那么这个包就是一个scoped package。scope就是指@符号和/符号之间的部分
`@scopr/project-name`

每个npm用户都有他们自己的scope
`@username/project-name`

你可以通过[CLI documentation](https://docs.npmjs.com/misc/scope#publishing-public-scoped-packages-to-the-public-npm-registry)了解更多关于scopes的信息。

## 更新npm并登陆

如果是第一次使用scoped模块的话，你需要一个版本高于2.7.0的npm而且需要在命令行界面重新登陆。
```
sudo npm install -g npm
npm login
```

## 初始化一个scoped包

创建一个scoped包，你只需要使用你的scope指定你的包名称package name
```
{
  "name": "@username/project-name"
}
```

如果你使用的*npm init*，需要在命令行添加你的scope参数
`npm init --scope=username`

如果你一直使用同一个scope，也可以在[.npmrc](https://docs.npmjs.com/files/npmrc)文件里设置这个参数
`npm config set scope username`

## 发布一个scoped包

Scoped包默认情况下是私有的。发布私有的模块，你需要拥有一个付费的私有模块[private modules](https://www.npmjs.com/private-modules)用户。

然而，发布scoped modules是免费的。需要设置access参数，在发布一个公共的scoped模块的时候。
`npm publish --access=public`

## 使用scoped包

使用scoped包就根使用普通包一样，只需要在使用package name的时候使用包含指定的scope

在package.json文件
```
{
  "dependencies": {
    "@username/project-name": "^1.0.0"
  }
}
```

在命令行界面
`npm install @username/project-name --save`

在一个require语句
`var projectName = require("@username/project-name")`

获取有关私有的scoped private modules，可以访问[npmjs.com/private-modules](https://www.npmjs.com/private-modules)