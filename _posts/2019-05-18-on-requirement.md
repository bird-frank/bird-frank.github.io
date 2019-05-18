---
layout: post
title: 关于需求的那些事
description: ""
category: 软件工程
tags: []
---

{% include JB/setup %}

# 什么是软件需求？

软件开发活动的目的是在一定的约束条件下、开发出能够解决用户问题的软件系统。

这个目的中蕴含着三个要素：

- 用户的问题是什么？
- 怎么解决用户的问题？
- 约束条件是什么？

这三个要求就构成了软件需求，搞清楚这三个要素就是需求分析阶段的任务。

这其中"要解决的问题"就是软件开发的总目标，它是其它一切内容的纲领。"怎么解决"是解决方案。约束条件就是一般所说的非功能性需求。

这里对"约束条件"多说几句，后面不再涉及。约束条件并不完全对应非功能性需求，因为有两个重要的约束条件一般不会出现在需求说明书上。一个是时间约束、一个是成本约束。时间约束和成本约束构成了最重要的约束条件。软件开发团队必须在时间和成本的双重约束下设计出能解决用户问题的解决方案，而软件开发的很多痛苦的根源就在于不合理的且刚性的时间和成本约束。当面领拍脑袋的预算、不能倒的后墙，软件开发就变成了带着镣铐在跳舞。

这里所说的“解决方案”也不是指技术解决方案，比如用什么样的数据库、什么样的语言、什么样的架构这类技术细节。而是要搞清楚软件需要什么样的功能、用户如何使用这些功能来解决自己的问题。

# 不要对用户言听计从

软件需求是整个软件开发活动的“纲”，起到引领性的作用。需求分析错了，整个软件开发活动鲜有能成功的。而需求分析中最致命的问题就是理解错用户的问题、设计出错误的解决方案。而犯下这个错误的最常见原因就是："对用户言听计从"。

用户提供的是问题，是用户需要软件系统来帮助解决的问题，但不要指望用户来给你解决方案。

现在用户在各类软件、APP 的包围中浸淫多年，对信息技术已经由"一无所知"进化到了"一知半解"。因此当用户碰到业务问题能够想到通过计算机软件、使用信息技术来帮助解决问题。这是好事。但是他们又常常会根据自己使用其它各类软件的经验设想一些新的功能"需求"、甚至操作界面的设计，这就不太好了。

用户设想的一些功能、界面往往不是最合理的——这里的合理是指用最有效、最经济的手段解决用户的问题。而这些假想的功能又往往掩盖了用户真正想要解决的问题。如果开发人员只是被动地"遵循"这些需求，即使最终开发出的软件完美地实现了用户的"功能"，但也不一定能解决用户的问题，至少不是以最合理的方式。

因此在需求分析中要多问“为什么？”。“为什么要这个功能？”“需要这个功能是想解决什么问题？”“为什么需要这个查询？什么情况下需要？”

问完“为什么”以后要准备好的问题是“换种方式、这样做行不行？”。不要怕用户说“不行”，常常用户的回答是“可以”，只要你能说清楚为什么你的方案能更好地解决他的问题。

当无法直接接触到最终用户时，比如在开发软件产品的时候，一般由公司里的某个部门或人（最常见的是产品经理）扮演用户的角色。理论上这个人应该比普通用户更了解信息技术、了解软件，因此有可能设计出合理的软件产品功能。但实际情况未必如此乐观，否则也不会发生"以拳头来决定系统功能"这种闹剧了。

![](http://ww3.sinaimg.cn/large/006tNc79ly1g35iphlln7j30g408paaf.jpg)

需求分析应该是一个多方参与、共同学习、互相补充的过程，而不是一方讲、一方听的单向信息传递的过程。学习、探讨的目的就是搞清楚上面说的三个要素。用户了解自己的问题，开发方则更了解什么样的信息技术和软件功能能解决用户问题。更重要的是，开放方要评估不同的解决方案需要的时间和金钱成本，从而在约束条件内选择最经济的解决方案最大限度地解决用户的问题。XP 提出的"用户决定 User Story 的优先级、开发团队估算完成需要的时间"正是这个分工思想的体现。

## 需求分析的技术

上世纪 90 年代 Ivar Jacobson 提出使用 UseCase（用例）进行需求分析的方法，后来被吸收入 Rational 公司的 RUP 中。这是我知道的第一个比较流行的做需求分析的方法。

到 2000 年，极限编程（XP）引入 UserStory，之后逐渐发展成几乎所有敏捷开发方法标准的需求分析方法。

UseCase 和 UserStory 都是从用户的角度描述用户是如何使用目标系统的。区别只是 UseCase 形式化的程度更高一些。比如在 UML 中有一套 UseCase 图的符号，还有 UseCase 文档的模板。而 UserStory 则更加轻量化、更加"随意"一些。

无论是 UseCase 还是 User Story 都有一个粒度大小的问题。就是一个 UseCase 或者 User Story 应该包括多少用户交互或"使用场景"。

![](http://ww3.sinaimg.cn/large/006tNc79ly1g35iws4n6eg304r08a3ya.gif)
(Alistair Cockburn 在 Writing Effective UseCase 中提出的 Use Case 的层次。)

在 UseStory 方面则是使用 Epic 来表示更粗粒度的功能或用户要完成的任务。还有使用 Initiative、Theme 来表示更大范围的功能与任务的。

随着 UserStory 的使用，人们也发现了"只见树木、不见森林"的问题。由于要求一个 UserStory 不能跨迭代（Iteration
or spring, 一般不超过两周），XP 更要求开发一个 UserStory 所需的人力不超过 2 到 3 个人天，因此一个大项目中 UserStory 的数量是非常多的。在这么多的 UserStory 中可能会迷失整个项目的大局。

![](http://ww3.sinaimg.cn/large/006tNc79ly1g35ixy5fvfj30yg0jeqf6.jpg)
(图片来源：<https://evolvingagile.wordpress.com/2017/04/15/implementing-change-using-kanban-part-viii/>)

于是有了 User StoryMapping，用于看清这个系统的全貌、同时规划每个版本交付的功能。下图是一个 UserStoryMapping 图的例子。从左至右表示用户使用系统完成某个任务的过程。从上到下表示功能的开发顺序（版本计划）。

![](https://manifesto.co.uk/wp-content/uploads/2017/05/user-story-mapping-4.png)
([图片来源](https://manifesto.co.uk/user-story-mapping/))

Alberto Brandolini 在 2013 年提出了 Event Storming 方法。这是一种分析复杂的业务问题域的 workshop format
(研讨会形式？)。Brandolini 认为在复杂的业务流程中会发生一系列业务事件。所以 Event Storming 从业务事件入手，然后分析导致业务事件发生的"决策"（或"指令"）。决策需要数据支撑，此谓"Read Model"。"决策"根据"业务逻辑"触发事件，一个事件又可能触发其它的业务事件。如此串起整个业务流程。

![](http://ww2.sinaimg.cn/large/006tNc79ly1g35jc25cdlj30ym0u0jyp.jpg)
([图片来源: A facilitators recipe for Event Storming](https://medium.com/@springdo/a-facilitators-recipe-for-event-storming-941dcb38db0d))

Event Storming 与 DDD 有很好的结合，可以帮助识别 Aggregate 和 Bounded Context。同时也能很自然地导出"事件驱动"的应用架构，契合微服务时代各服务之间的降低耦合度的需要。

UserStrory 和 Event Storming 是可以结合使用的。具体如下图所示。

![](http://ww4.sinaimg.cn/large/006tNc79ly1g35jbmyghuj30iq0paq8h.jpg)
([图片来源：Embed event storming in your agile toolset](https://medium.com/@kevin.van.ingen/mix-event-storming-in-your-agile-toolset-437a54939aeb))

简单说就是先确定系统要解决的业务问题。然后使用 Event Storming 分析业务流程和问题域，这个过程中可以细化出 User Story。然后使用 User Story 规划系统版本计划，由此就可以得到待开发的 Backlog。

# “我需要需求文档的模板。”“不，你不需要。”

UseCase 在流行的过程中，使用者常常陷入"UseCase 的文档模板应该是怎样的"、"这两个 UseCase 间到底是扩展关系还是使用关系"，诸如此类的辩论和纠结中。不少公司也设计了自己的或复杂或简单的 UseCase 文档模板。

相对于 UseCase，User Story 更"轻量"，更"不正式"。XP 中 User Story 是写在索引卡片上的。一般只有一句话，采用这样的格式：

"As a ...... I want to ...... So that ......"。

![](http://ww4.sinaimg.cn/large/006tNc79ly1g35jschg44j30dw0afwf3.jpg)
([图片来源: User story cards for web writers](https://4syllables.com.au/articles/user-story-cards/))

填空的部分分别表示"用户角色"、"执行的动作"、"执行该动作的目的（或对用户的价值）"。

也有公司制定了比较正式的 User Story 卡片的格式。但是用 Ron Jeffries(XP 的发明人之一)的话说，当你考虑 UserStory 的正式格式的时候，你就已经错了。

![](http://ww2.sinaimg.cn/large/006tNc79ly1g35jkzlq64j30gk0c0dho.jpg)

User Story 不是正式的需求文档。User Story 卡片只是一个提示，表明"这里有一段对话"。用户或者 ProductOwner(XP 术语)和开发者之间通过对话、讨论获得对"软件应该达到什么目标"这个问题的深入理解。

Event Storming 也是一种非常轻量级的、"不正式"的方法。要求把尽可能全的人邀请到一间会议室中，但是除了设置放有咖啡、饮料和点心的桌子以外，没有会议桌、也没有椅子。所有人都站着，拿着不同颜色的便签纸。不同颜色代表"事件"、"指令"、"Read
Model"等不同概念。每个人都可以写了标签然后贴到墙上。

![](http://ww4.sinaimg.cn/large/006tNc79ly1g35jlrt487j31hd0u0dzj.jpg)
([图片来源: A facilitators recipe for Event Storming](https://medium.com/@springdo/a-facilitators-recipe-for-event-storming-941dcb38db0d))

那么需求文档到底应该是什么样的呢？

最好的需求文档就是一套验收测试的用例，通过这些测试用例表明完成了用户需要的功能。比验收测试用例更好的文档就是能够
**自动执行** 的验收测试用例。

> The conversation ideally ends with a clear statement of the acceptance
> criteria for the story, answering the question "How will you know that
> we have done what you're asking?" The answer comes, again ideally, in
> the form of one or more executable tests which, when they work, show
> that the story is done.
>
> <https://ronjeffries.com/xprog/blog/how-should-user-stories-be-written/>

验收测试用例应该采用"举例子"的方式。例如在一个在线购物系统中，对于是否应该给用户免运费优惠的规则，测试用例应该列出免运费和不免运费的各种情况。

![](http://ww2.sinaimg.cn/large/006tNc79ly1g35jndv0mhj30b90dwdgc.jpg)

相关的概念还包括：

- [Acceptance Test DrivenDevelopment](https://www.agilealliance.org/glossary/atdd)
- [Behavior DrivenDevelopment](https://www.agilealliance.org/glossary/bdd)

无论是 User Story 还是 Event Storming，都是包含大量对话、讨论的过程。因此也有人提出进行全程录像，以保留讨论过程中的所有细节、包括表情和肢体语言的方法。这是比任何传统需求文档都能最大限度保留细节的方法。

# 参考资料

- [User Stories](https://www.mountaingoatsoftware.com/agile/user-stories)
- [Introducing Event Storming (by Alberto Brandolini)](http://ziobrando.blogspot.com/2013/11/introducing-event-storming.html)
- [Using 'Event Storming Practice'​ @ Heritage Bank](https://www.linkedin.com/pulse/using-event-storming-practice-heritage-bank-sandra-arps/)
- [Modelling Reactive Systems with Event Storming and Domain-Driven Design](https://blog.redelastic.com/corporate-arts-crafts-modelling-reactive-systems-with-event-storming-73c6236f5dd7)

- [《用户故事与敏捷方法》](http://product.dangdang.com/20834196.html)
- [《用户故事地图》](http://product.dangdang.com/23939087.html)

- [《Specification By Example》](http://product.dangdang.com/27802181.html)
- [Alberto Brandolini - 50,000 Orange Stickies Later (Youtube)](https://www.youtube.com/watch?v=1i6QYvYhlYQ)
- [Event Storming demo & discussion (Youtube)](https://www.youtube.com/watch?v=xIB_VQVVWKk&t=6s)
- [microXchg 2018 - Designing Reactive Systems with Event Storming - Lutz Huehnken](https://www.youtube.com/watch?v=Xh6Ts19M6rg)
