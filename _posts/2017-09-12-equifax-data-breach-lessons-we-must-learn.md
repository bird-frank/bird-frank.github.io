---
layout: post
title: "Equifax数据泄漏事件: 我们必须吸取的教训"
description: ""
category:
tags: [技术,翻译]
---

{% include JB/setup %}

翻译自[EQUIFAX DATA BREACH: LESSONS WE MUST LEARN](http://www.agileadvice.com/2017/09/08/agilemanagement/equifax-data-breach-lessons/)

译者注：Equifax是美国最大的征信机构之一。[关于Equifax数据泄漏事件的中文报道](http://gold.hexun.com/2017-09-12/190828510.html)

### 怎样的“糟糕环境”导致了Equifax数据泄漏事件？


首先让我们回顾一下：据报道黑客从Equifax的系统中窃取了未透露数量的敏感数据。黑客
搜集了超过1.43亿人的姓名、地址、信用卡、驾驶证号、银行交易记录。（你的信息也可能
包含其中！）

在这里我要说明一下，新闻虽然刚刚被曝光，但是问题却是长期存在的。安全漏洞已经存在
（可能）数年之久，并且我确信Equifax管理层中的一些人早就知道这些。

Equifax！我们不是在讨论什么由几个菜鸟程序员编写的某个高中项目。我们在说的是世界
上最受信赖的组织之一。我们在说的是一个其存在目的（它的所有业务！）就是要保护我们
的“抵押物”（collateral）的公司。这应该是一个地球上经费最充足、最最安全、技术最
最先进的公司之一。

### 但这新闻并未让我感到惊讶。因为……

我是教授Scrum的老师，我的教室里经常有来自像Equifax这样的公司的学生。我每天都会听
到他们的故事：

> “我们的经理不提供我完成工作所需要的工具。”

> “我们的经理不理解交付高质量软件所需要的时间。我们总是被迫凑合行事以满足拍脑袋
> 出来的、完全不现实的最终期限。”

> “我们没有权力决定实施方案。我们必须遵照设计师和管理层说的去开发，即使我们知道
> 他们的决定糟糕透顶（to be rotten）。"

> “我们的经理从来不过问质量，只是问我们‘你们什么时候完成？’”

问题的核心是：像Equifax这样的公司雇佣了有技术专长的人，但是他们的建议被忽略，他
们的实施决定(implementation decisions)也不被信任。

### 一些值得考虑的重要问题：

1. Equifax没有足够的钱来雇佣优秀的技术人员吗？

不。他们的办公室里有世界上最好的程序员。我经常性地在教师里遇到他们，我确信
Equifax的技术人员几年来一直在警告他们的经理安全漏洞和技术缺陷的存在。我同样确信
这些经理忽略了这些警报，然后逼迫技术人员去交付有缺陷的代码。

2. Equifax没有足够的钱来构建高质量的系统吗？

不。据我所知，他们现有的合同将长期维持他们的运营。并且正如前面所说，保护我们的数
据正是公司存在的理由。人们设想他们能做好这件事。我想他们所有的时间都应该被用来构
建高质量的系统。

3. Equifax没有足够的财力来投资合适的工具、以及安全和质量测试所需要的培训吗？

不。这样的技术和工具是很容易获得的，价格也不贵（即使黑客也能负担得起）。Equifax
的经理们以“太贵了”为理由否决了培训、工具和升级的预算……我在想数据泄露的代价是
多少？

4. 最后是我最喜欢（favorite）的问题：是黑客们更聪明吗？

绝对不是。不过他们（黑客）更加专注，他们用更好的技术和工具武装自己来进行渗透测试。
根据我自己作为黑客的经验（呃……广义上的黑客），只要我们去找，安全漏洞在我们身边
到处都是。Equifax只是根本没有去找！

### 我们该怎么去做呢？

首先，我很清除这不是技术或财务问题。这是文化（问题）。我早就发现了。优秀的产品开
发团队被官僚主义包围，而无法获得足够的支持。优秀的程序员团队不受信任，因此不能阅
读公司系统的源代码——是的，我知道这听上去很疯狂！程序员被迫对他们发现的安全漏洞保
持沉默。经理们忽略掉安全问题的解决方案，理由总是“提升安全性不是当前的优先任
务。”或者“我们知道这里有些安全问题，我们正在与供应商或外部机构（outside
agencies）讨论解决它们。”或者“我们已经在下一季度安排了提升安全性的预算；现在让
我们先集中精力实现这些新功能。”经理们关心最后期限更甚于产品质量。经理们仔细计算
开发人员在一个任务上花费的小时数，然后将质量保证和测试工作外包出去！经理们在制定
计划上花费了无尽的时间，然后把实施工作压缩到局促的预算和时间表中。很明显，大量的
精力被用于完成计划，但是让软件“正确”却不是优先任务。这样的问题我还能列出很多。

如果你感兴趣在Equifax工作是怎样的经验，你只要想想呆伯特漫画。我是认真的。呆伯特
的滑稽并不是因为它是虚构的，它的滑稽在于他是真实的。很可悲。类似Equifax这样的公
司中，技术人员和客户坐在管理“剧院”的后排（意指在企业管理工作中居于无足轻重的地
位？——译者注）。首先，我们可以通过向技术人员提出这样一个简单的问题来纠正这一错误：
“你们当中有谁曾经提出过关于‘技术债’（指软件中已知的、未解决的技术问题）的问题，
然后被经理或上级忽视了？”这个问题将挖掘出被经理们定为低优先级的软件缺陷；被否决
的自动化测试技术培训的预算；在完成部署准备前就被宣布为“完成”的项目。——换句话说，
这个问题将揭示经理们阻挡质量之路的（可以被纠正）方式。

其次，Equifax的最高管理层需要参加自动化测试的速成课程。是的，我说的是 *最高管理
层* !他们亲眼看到并理解以下事实非常关键:

自动化测试比手工测试更便宜、更有效得多；所有的缺陷都是可以在进入生产环境前被发现
和修正的；质量不是可以被外包的东西；达到零缺陷的技术是广为人知的、可教授的、可重
复的、经过验证的。无疑的，我指的是类似“测试驱动开发”、连续集成、重构和“蜂巢式
开发”(Swarming)。这些技术课题组成了我们的“认证Scrum开发者”课程的大部分内容
（不好意思，插入广告了——原作者）

第三，技术人员不应该再像绵羊那样（驯服）。目前为止，在这篇文章中我对经理们非常严
厉，当然，了解我的人都知道我一向看不上无能的管理。但是我经常看到聪明的、非常好的
开发者交出拙劣的代码——他们也许是在巨大的压力下、并且违心地这样做，但是归根结底这
是谁的代码呢？程序员们！我理解你们常常感到陷入“数量胜过质量”的模式，并且经常被
你们的经理逼迫着粗制滥造。我知道……我理解……很容易把最后期限当成不可修正的真理、
并且经理总是会滥用他们的权力。但事实是，程序员们，你们承担所有的责任，因此你们必
须专业。你们要说“不”并且要求为交付高质量的软件所需要的所有条件。你们是最接近代
码的人，因此你们直接为用户的安全和身心健康负责。

### Equifax和所有的企业，这里我作为们的用户、股东和客户对你们说：

Equifax非常悲惨地失败了，面临必将接踵而来的所有诉讼官司，他们罪有应得，从最高领
导到开发者，所有人（谁也逃不过）

很多社会成员被无辜地牵连其中。我们中的很多人不是你们的直接客户。例如，我就不是
Equifax的直接客户——没有人选择Equifax作为他们的个人代理。但是，我们的银行和政府选
择了Equifax（搜集我们的征信信息——译者）。这带来了一个问题，如果我是Equifax的直接
客户，我今天就可以打电话给他们关闭我的账户。但是现在我不能这样做。作为个人我能做
的只有联系我的银行、放款人、保险代理来做出改变。（是的，我会这样做，说到做到）

然后，更大的问题是我们的命运全都交在你——软件开发者——的手中。我说的是在我们的汽车、
心脏监控器、地铁系统、空中交通管制系统、银行中的软件——这是非常严肃的事情！我们必
须能信任这些系统，因为我们的生命和安全全赖于此。我们必须信任你，即使我们不会也不
想认识你。

一个黑客朋友曾经说：“如果无人驾驶汽车（软件）没有全面的自动测试覆盖，这不是我想
要的未来。”

在这个年代，低质量是不可容忍的。

请转发！（——原作者）

（转发请注明出处，并保留英文原文链接。）
