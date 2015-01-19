---
layout: post
title: osx quickview plugin
description: ""
category:
tags: []
---

{% include JB/setup %}

OSX的QuickView实在实在是个非常有用功能。不仅在Finder里可以用，在一切选
择文件的对话框里、在邮件客户端查看附件的时候都可以用。不过OSX自带的
QuickView插件能支持的文件格式还比较有限，这里推荐更多的一些插件。

如果英文好的话可以直接看githubs上的
[这个帖子](https://github.com/sindresorhus/quick-look-plugins)

我安装了其中的两个插件：

#### QLStephen
预览任意文件名后缀或压根没有后缀的文本文件。

安装方法：

``` sh
brew cask install qlstephen
```

#### QLMarkdown

预览Markdown文件。而且是预览生成的HTML，而不是Markdown的源文件。因为要先将Markdown转换成HTML，所以不算太
“quick”。

安装方法：

``` sh
brew cask install qlmarkdown
```

根据初步的测试，它似乎可以支持github的Markdown扩展语法。下图就是用这个
插件预览这篇文章的原始md文件的效果。其中的两段shell脚本用的是github 扩
展的"```"标记。

![qlmarkdown](http://i46.photobucket.com/albums/f136/bird_frank/5C4F5E555FEB71672015-01-194E0B534891347_zpsb4a49f38.jpg)
