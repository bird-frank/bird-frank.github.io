---
layout: post
title: Use org-protocol on Mac OS
description: ""
category:
tags: [emacs]
---
{% include JB/setup %}

``org-protocol.el``是一个elisp程序，它可以解析来自emacsclient的输入，触
发预先配置好的自定义动作。``org-protocol``接受的输入应该是一个符合URL格式的字
符串（作为``emacsclient``的``FILE``参数），使用```org-protocol``作为协议名
称，具体格式如下：

``org-protocol:/sub-protocol:/URL/TITLE``

``sub-protocol``是由用户自定义的，每个``sub-protocol``可以关联各自的处理程序。
``org-protocol``预定义的四个``sub-protocol``是：

+ ``store-link`` : 保存一个``org-link``，并将``URL``加入kill-ring。
+ ``capture`` : 使用 ``org-capture`` 将传入的内容加入一个``.org``文件。
+ ``remember`` : 使用``org-remember``保存传入的内容。由于``org-remember``已经被
``org-capture``代替，所以这个只是为了向前兼容。
+ ``open-source`` : 打开并编辑一个本地文件（由``URL``指定）。

虽然预定义的四个``sub-protocol``都使用了OrgMode的功能（``open-source``不算），你
自己写的``sub-protocol``的``action``完全不受这个限制。

[``org-protocol``官网](http://orgmode.org/worg/org-contrib/org-protocol.html)有
详细的说明。

对``org-protocol``的一个典型用户法是在浏览器中配置一个“bookmarklet”，使用时只要选
中网页中感兴趣的内容，然后运行这个bookmarklet就能将选中的内容使用预先定义好的
``org-capture``模板抓到指定的``.org``文件中，从而实现对网上内容做摘抄的功能。

在Stackoverflow的
[这个回答](http://stackoverflow.com/questions/7464951/how-to-make-org-protocol-work/12751732#12751732)
中有比较详细的步骤描述。但是这个步骤是针对Linux的，在MacOS上不适用的。

``org-protocol``的设计思路是使用操作系统的自定义URL协议处理程序的机制工作的，即
预先配置``org-protocol``协议的处理程序（``emacsclient``），然后在bookmarklet中打开
``org-protocol``协议的URL（如上文所示的格式）(或用其它方式打开)，就会运行``emacsclient``，从而在
``emacs``中触发``org-protocol``。在Linux上，可以配置任何可执行文件作为自定义URL
协议的处理程序，但是在MacOS中只能使用打包好的Application，这样就不能直接使用
``emacsclient``了。

在``org-protocol``的官网上介绍了一个
[EmacsClient.app](https://github.com/neil-smithline-elisp/EmacsClient.app)，这个
App已经配置为能够处理```org-protocol```协议。但是这个App并不是调用
``emacsclient``，而是似乎直接调用了``Aquamacs``，因此它要求系统中预先安装了
``Aquamacs``。而如果系统中安装的是别的``emacs``版本，比如我用``homebrew``安装的
版本，则这个App不能工作。

幸好，根据
[这篇文章](https://yourmacguy.wordpress.com/2013/07/17/make-your-own-url-handler/)
，自己写一个自定义URL的处理程序，并且调用``emacsclient``并不是件困难的事情。

简单说，只要用“脚本编辑器”写这样一个简单的``Apple Script``脚本:

```applescript
on open location this_URL
	do shell script "/usr/local/Cellar/emacs/HEAD/bin/emacsclient " & this_URL
	tell application "Emacs" to activate
end open location
```

注意修改其中``emacsclient``的安装路径。

然后将这个脚本保存为一个“应用程序”（Application），并保存在``/Applications``目录下。

在Finder中找到刚才保存的应用程序，显示包内容，找到``Info.plist``文件，在文件中加入以下内容：

```xml
<key>CFBundleURLTypes</key>
<array>
  <dict>
    <key>CFBundleURLName</key>
    <string>SysPref Handler</string>
    <key>CFBundleURLSchemes</key>
    <array>
      <string>org-protocol</string>
    </array>
  </dict>
</array>
```

这几行就是表明这个应用可以处理``org-protocol``这个URL protocol。双击运行这个应用可以使该应用生效。

最后介绍另一个有用的elisp程序：[``org-protocol-capture-html``](https://github.com/alphapapa/org-protocol-capture-html)，它可以将通过bookmarklet摘取的``html``内容通过``pandoc``转换为``org-mode``的格式。在它的主页上有详细的配置说明。

