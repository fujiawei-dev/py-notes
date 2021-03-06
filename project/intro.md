---
date: 2020-12-01T13:10:34+08:00  # 创建日期
author: "Rustle Karl"  # 作者

# 文章
title: "如何开始一个 Python 项目工程"  # 文章标题
url:  "posts/py/project/intro"  # 设置网页永久链接
tags: [ "python", "project", "intro" ]  # 自定义标签
series: [ "Python 学习笔记"]  # 文章主题/文章系列
categories: [ "学习笔记"]  # 文章分类

# 章节
weight: 20 # 排序优先级
chapter: false  # 设置为章节

index: true  # 是否可以被索引
toc: true  # 是否自动生成目录
draft: false  # 草稿
---

## 项目布局

项目结构应该保持简单，审慎地使用包和层次结构：过深的层次结构在目录导航时将如同梦魇，但过平的层次结构则会让项目变得臃肿。

一个常犯的错误是将单元测试放在包目录的外面。这些测试实际上应该被包含在软件的子包中，以便：

- 不会偶尔被 setuptools （或者其他打包库）作为 tests 顶层模块自动安装；
- 能够被安装，且被其他包用于构建自己的单元测试。

推荐布局：

```shell
project
│  README.md
│  requirements.txt
│
├─etc
├─bin
├─tools
├─docs
│      conf.py
│      index.md
│      quickstart.md
│
└─project
    │  cli.py
    │  storage.py
    │  __init__.py
    │
    └─tests
            test_cli.py
            test_storage.py
            __init__.py
```

一个常见的设计问题是根据将要存储的代码的类型来创建文件或模块。使用 functions.py 或者 exceptions.py 这样的文件是很糟糕的方式。这种方式对代码的组织毫无帮助，只能让读代码的人在多个文件之间毫无理由地来回切换。

此外，应该避免创建那种只有一个 `__init__.py` 文件的目录，例如，如果 `hooks.py` 够用的话就不要创建 `hooks/__init__.py`。如果创建目录，那么其中就应该包含属于这一分类 / 模块的多个 Python 文件。

## 版本编号

```
N[.N]+[{a|b|c|rc}N][.postN][.devN]
```

- 1.2 等于 1.2.0，1.3.4 等于 1.3.4.0，以此类推。
- 与 N[.N]+ 相匹配的版本被认为是最终版本。
- N[.N]+aN （如 1.2a1 ）表示一个 alpha 版本，即此版本不稳定或缺少某些功能。
- N[.N]+bN （如 2.3.1b2 ）表示一个 beta 版本，即此版本功能已经完整，但可能仍有 bug。
- N[.N]+cN 或 N[.N]+rcN （如 0.4rc1 ）表示候选版本（常缩写为 RC ），通常指除非有重大的 bug，否则很可能成为产品的最终发行版本。尽管 rc 和 c 两个后缀含义相同，但如果二者同时使用，rc 版本通常表示比 c 更新一点。
- .postN （如 1.4.post2 ）表示一个后续版本。通常用来解决发行过程中的细小问题（如发行文档有错）。如果发行的是 bug 修复版本，则不应该使用.postN 而应该增加小的版本号。
- .devN （如 2.3.4.dev3 ）表示一个开发版本。因为难以解析，所以这个后缀并不建议使用。它表示这是一个质量基本合格的发布前的版本，例如，2.3.4.dev3 表示 2.3.4 版本的第三个开发版本，它早于任何的 alpha 版本、beta 版本、候选版本和最终版本。

## PEP 8

- 每个缩进层级使用 4 个空格。
- 每行最多 79 个字符。
- 顶层的函数或类的定义之间空两行。
- 采用 ASCII 或 UTF-8 编码文件。
- 在文件顶端，注释和文档说明之下，每行每条 import 语句只导入一个模块，同时要按标准库、第三方库和本地库的导入顺序进行分组。
- 在小括号、中括号、大括号之间或者逗号之前没有额外的空格。
- 类的命名采用骆驼命名法，如 CamelCase ；异常的定义使用 Error 前缀；函数的命名使用下划线分隔的小写字母，如 separated_by_underscores ；用下划线开头定义私有的属性或方法，如 _private。

```
```

## 


