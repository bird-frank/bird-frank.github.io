---
layout: post
title: 我为什么使用EMACS
description: ""
category:
tags: []
---

这是我在“知乎”上针对[为什么这么多人喜欢使用 Vim 或 Emacs？](http://www.zhihu.com/question/19712884)这个问题的回答。

---

我基本没有使用过vim，因此只针对Emacs的情况来说。其实最初是想针对
[为什么有的程序员极度推崇 Vim 和 Emacs，却对 IDE 嗤之以鼻？](http://www.zhihu.com/question/21504638)这个问题进行回答的，
但是第一，我并不会对任何IDE或使用IDE的人“嗤之以鼻”，其次我也不认为一个认真的Emacs用户会对IDE嗤之以鼻，因此就没法回答这个
以“为什么”开头的问题了。后来发现我想说的内容针对现在这个问题更合适，所以就发到这里来啦。

先说说Emacs和IDE比较的问题。Emacs不是一个简单的文本编辑器，能做到事情远远超过IDE。如果只用Emacs来编写代码，那么相当于拿
了一把瑞士军刀却只用它的主刀片。

说说我自己吧，以前我用Eclipse写J2EE软件，后来用Textmate写RoR软件；用Word写文档，还要一个工具来画UML图，导出成图片后再插
入Word文档。到了Mac上以后改用Pages，流程还是差不多。用Evernote记笔记，用过一些GTD的软件来做任务管理，尝试过几次写博客，都
是在浏览器里直接编辑的那种。

目前这些任务都在Emacs里完成啦：

+ RoR的代码自然在Emacs里完成，前两个月刚在Emacs里配了Android的开发环境开始学习Android。iOS的软件还是用xCode，主要因为目
前基本不做iOS的开发，只是偶尔看看别人的代码，做些小修改，因此暂时没有在Emacs里配开发环境。
+ 技术文档用org-mode写，然后导出成PDF；UML图用PlantUML画，在org-mode里一气呵成，再也不用在不同软件间倒来倒去了。而且可以
  在文档里插入带语法高亮的源代码，这一点我现在也不知道怎么在Word或Pages来实现。
+ Evernote的编辑功能实在太弱，又不支持Markdown，因此目前正在逐渐用org-mode来代替。用了deft插件，搜索笔记非常方便。
+ 博客的话用jekyll，自然也是在Emacs里用Markdown写，然后再发布到github上。这个答案就是在Emacs里写的，稍后只要做下```git
  push```就可以发布到我的博客上去了。
+ 任务管理也是用org-mode，接下去准备尝试把日程管理也从Calendar切换到org-mode来。

所有这些任务都有一个共同点，就是他们都有很多文字输入和编辑工作。如果象以前那样要用不同软件来完成的话，每个软件的编辑功能
多少都有些不同，强弱差别非常大。而统一使用Emacs以后，虽然Emacs的学习曲线有些陡，但是只要学会了以后，在所有这些任务中都能
用到。而且因为专注一个软件，每天大量的时间使用它，很快就很学会和数量使用了。

Emacs有强大的定制功能，可以完全根据个人的习惯、喜好来把它“调教”成个人专属的功能。而且这种“定制化”的投资对于上述的所有任
务都有价值，投资回报超高。

可以说使用Emacs完成的任务越多，用在学习和定制化上的“投资”就越有价值。

使用Emacs的另一个原因是为了贯彻KISS（Keep It Simple）原则。有人可能觉得Emacs超复杂，并且因此而望而却步，不愿意去学习它。
但是一旦学会了，用一个Emacs来代替一堆其它软件的时候，你就会发现生活一下子简单了很多。不再需要面对很多软件上面那些根本不会用
到的菜单、按钮，而只专注于完成日常任务所需要的那些最常用的功能上，然后用最有效率的方式去完成它们。






{% include JB/setup %}