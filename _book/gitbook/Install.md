# 简介

GitBook 是什么？其实用一句话就可以概括，它是一个能将使用 MarkDown 语法的 md 格式文档，快速制作成各种格式电子书的工具。

常被用于编写文档或者电子书，特点是方便简洁，易于使用。只要熟悉轻量级标记语法的 MarkDown 语法，就能使用 GitBook 来制作各种格式的电子书。接下来笔者就来分享一下自己使用 GitBook 的方法和经验，会分类来介绍，感兴趣的可以关注笔者关于 GitBook 这个系列的文章。

# 环境安装

## 下载和安装 Node.js

- [官网](https://nodejs.org/)
- [中文镜像网站](http://nodejs.cn)

> 注意: 基于截止到目前的 GitBook V3.2.3 版本，需要使用 NodeJs 的 v10+ 版本，否则会产生各种报错。

## 安装 gitbook-cli

```bash
$ npm config set registry http://registry.npm.taobao.org
$ npm install gitbook-cli -g
```

安装完成之后，可以通过如下命令进行验证 GitBook 是否安装成功：

```bash
$ gitbook -V
CLI version: 2.3.2
GitBook version: 3.2.3
```

# 总结

总之，GitBook 就是一个电子书生成工具，类似与 Git，Git 是一个代码仓库管理工具，用于管理代码文件，并且可以生成代码的变更记录，同时具备上传这些文件和变更记录到指定的服务器。那么同理，我们也可以结合 GitBook 和 Git 来管理我们的文档和生成的电子书文件。当然，本书主要介绍 GitBook，关于 Git 的相关知识，可以参考其他相关的教程。