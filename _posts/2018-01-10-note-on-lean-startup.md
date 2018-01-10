---
layout: post
title: 《精益创业》读书笔记
description: ""
category:
tags: []
---

{% include JB/setup %}

**TL;DR** 创业过程中基于假设和猜想制定计划是没有问题的；关键是如何用最小的代价对假设和猜想进行测试。

----

[《The Lear Startup》](https://www.amazon.com/Lean-Startup-Entrepreneurs-Continuous-Innovation/dp/0307887898/ref=sr_1_3?ie=UTF8&qid=1515587558&sr=8-3&keywords=Lean+Startup) 作者：Eric Ries，2011年出版。中文版 [《精益创业:新创企业的成长思维》](https://www.amazon.cn/dp/B008MIFWJG/ref=sr_1_1?ie=UTF8&qid=1515587650&sr=8-1&keywords=精益创业)

> A Startup is a human institution designed to create a new product or service under conditions of extreme uncertainty.
>
> 创业组织是一个在高度不确定条件下创造新的产品和服务的组织。

这个定义中的关键点是**高度不确定 (extreme uncertainty)**。由于这个特点，传统的管理方法、原则、手段都可能不适用，都需要被重新检验。

由于**高度不确定性**的存在，由于是创造新的产品和服务，因此没有现成的经验可以照搬，创业过程中不可避免地需要依赖大量的假设和猜想来定义企业的愿景、制定策略、设计产品。但是这些假设和猜想也会带来巨大的风险。因此快速地、低成本地对这些猜想和假设进行测试就成为创业成功的关键。

创业的过程是一个学习的过程、一个学习如何构建一个可持续的业务的过程。这种学习是可以通过科学的方法进行验证的。经常进行的、精心设计的实验使创业的企业家（entrepreneurs）能够测试商业愿景、计划中的每一个假设和猜想。这种可验证的学习过程可以证明创业团队已经获得了关于自身当前和未来的商业预期的有价值的知识。

创业的基础活动是“构建（Build）——测量（Measure）——学习（Learn）”的循环。根据“点子(idea)”构建出产品，然后测量用户的反馈，从用户的反馈中学习。

在初期为了测试某种假设和猜想而设计产品，测试的结果可能有两种：原先的假设成立或不成立。如果假设成立，那么可以设计新的测试、验证更多的假设。在这个过程中对用户的需求有更清晰的理解和认识。如果假设不成立，那么需要对原有的计划进行修正、做小的业务转型，如果制定商业计划的根本性假设被验证为错误，那么就需要考虑整体转型。

由于存在假设和猜想被证明不成立的情况，存在需要转型的风险，因此需要避免基于未验证的假设投入过多的资源，这个资源包括人力、资本和时间。比如，如果商业计划的盈利模型高度依赖产品的定价，那么不测试市场对这个价格的接受程度就投入上千万的开发运营费用，之后才发现产品根本卖不了这个价格，那么上千万的投资都可能打水漂。

创业团队的每一个产品都是实验，这些实验的结果就是学会如何构建一个可持续的业务。

最重要的两类假设是“价值假设”和“增长模型”假设。“价值假设”是关于“用户是否认可我们的产品带来的价值”。“增长模型”是关于“用户数量将如何增长”。

为了加快“Build-Measure-Learn”循环的速度，每次只制造能够满足当前测试目的的MVP（最小可行产品）。这一点与“测试驱动开发”的“只写能使当前测试通过的代码”的原则高度吻合。（关于“精益创业”和“敏捷软件开发”的关系需要另外的文章来说明）。最小的投入、最快的速度。

> the goal of MVP is to begin the process of learning, not end it. ... Its goal is to test fundamental business hypotheses.
>
> MVP的目标是开始学习过程，而不是结束学习。它的目标是测试最基本的商业前提（假设）。

在书中举了不少MVP的例子。

Groupon最早的产品只是一个博客网站，在博客文章中介绍产品和团购信息、通过Email接受订单。当Groupon一天卖出500张“寿司优惠券”的时候，它使用FileMaker手工制作包含优惠券的PDF文件，然后人工将PDF文件通过电子邮件发送给客户。

Dropbox最开始时的MVP是演示产品功能的一段视频，而这个时候产品根本还没有开发出来。视频公布在Youtube上，然后接受用户参加Beta测试的报名。通过报名用户的数量变化获知用户是否欢迎视频中展示的功能。（我的理解：MVP应该能获取用户直接的、明确的反馈。因此单独的产品原型、UI设计等不能成为MVP。如果Dropbox只是发布视频，而没有“申请成为Beta测试用户”的设计则不能算是个好的MVP，因为无法对用户的反馈进行“测量”）。

一家叫做“Food on the Table”的公司，他们设计的业务是根据用户的餐饮习惯和喜好、以及用户附近商店出售的生鲜食品的种类和价格制定菜谱和购物清单，包括在哪家店购买最划算的信息。他们最初只发展了一位客户，公司的产品VP亲自到这个客户家附近的超市和杂货店调查商品价格，然后将菜谱和购物清单亲自送上门，并当面收取服务费。在这个面对面服务的过程中他们对于自己的产品所需要的特性和功能有了越来越清晰的了解。

书中的部分“格言”：

> What if we found ourselves building something that nobody wanted? In that case what did it matter if we did it on time and on budget?
>
> 如果我们造出来的东西没有人要，按时按预算完成又有什么意义？

> Until we could figure out how to sell and make the product, it wasn't worth spending any engineering time on.
> 
> 在我们了解如何销售和制造产品之前，不值得花费任何工程时间。

> Success is not delivering a feature; success is learning how to solve the customer's problem.
>
> 交付一个功能不是成功；学到如何解决用户的问题才是成功。

> Remember, planning is a tool that only works in the presence of a long and stable operating history.
>
> 记住！只有在具备长期、稳定运营历史的条件下，“计划”才是有效的工具。

> The first challenge for an entrepreneur is to build an organization that can test these assumptions systematically. The second challenge, as in all entrepreneurial situations, is to perform that rigorous testing without losing sight of the company's overall vision.
>
> 创业企业家的第一个挑战是建立一个能够系统地测试这些（商业计划中的）假设的组织。第二个挑战，和其它企业环境中一样，是在进行这些细碎的测试时不失去对公司总体发展的长远视野。

> If we do not know who the customer is, we do not know what quality is.
>
> 如果我们不知道用户是谁，我们也无法定义质量标准。（客户对质量的理解可能和我们设想的很不一样）。

最后的话：为什么没有在2012年看到这本书！！！


