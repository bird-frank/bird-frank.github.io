---
layout: post
title: 使用Emacs和org-mode管理所有的口令和密码
description: ""
category:
tags: []
---

使用的工具和软件：

+ Emacs
+ org-mode
+ gpg

### 安装[gpg](https://www.gnupg.org)

首先下载[GnuPG for OS X](https://sourceforge.net/p/gpgosx/docu/Download/)的最新版。

下载的是个DMG文件，挂载之，然后执行```Install.pkg```。

如果想用Homebrew安装的，那么需要执行：

``` sh
brew install gnupg2
```

### 生成加密密钥

```
gpg --gen-key
```

关于gpg生成密钥的详细步骤见[“GPG入门教程”](http://www.ruanyifeng.com/blog/2013/07/gpg.html)



{% include JB/setup %}
