---
layout: post
title: 2017年我们如何选择前端框架
description: ""
category:
tags: [前端,翻译]
---

{% include JB/setup %}

（翻译自英文博客 [Choosing a frontend framework  in 2017 ( By Taras Mankovski)](https://medium.com/this-dot-labs/building-modern-web-applications-in-2017-791d2ef2e341) , 原文需要翻墙才能看。插图均为原文所配。）

![](http://o9si8u3ts.bkt.clouddn.com/2017-07-15-1-T551HACMn9A95dnwpPK-eQ.png)

在过去的七年中，前端框架生态系统得到了很大的发展。在如何构建和维护大型应用方面我们学到了很多。一些创新的想法改变了我们构建Web应用的方式，其它一些因为没什么效果而被抛弃。

在这个过程中，一些夸大的宣传和互相矛盾的观点使得框架的选择变得困难。当我们为一个负责长期维护这样的应用的组织选择框架时这种选择尤其艰难。

在这篇文章中，我将首先回顾一下我们对于现代Web应用构建方法的理解是如何演进的，然后对如何选择使用的技术提些建议。

首先我将沿着记忆的河流回溯到这样一个时刻，那时诞生了第一个使得构建Web应用更有编程感觉的程序库。Backbond.js 在2010年10月第一次发布，2013年3月发布了1.0版。这是第一个被广泛使用的、引入了模型与视图分离概念的Javascript程序库。

![](http://o9si8u3ts.bkt.clouddn.com/2017-07-15-1-vqOV_K_r66lUwdFeABCWEQ%402x.png)
(Angularz中模型与视图见的关系，来源 [](http://backbonejs.org) )

Backbone的模型代表了数据和业务逻辑。数据发生改变时它们向视图发送通知。当一个变化事件被触发，视图负责将变化反应到DOM中。Backbone“模板不可知”（译者注：原文template agnostic，我不熟悉Backbone，不清楚这里指Backbone不强制适用视图层模板，还是不强制使用某种视图层模板。）。它将更新DOM的工作完全留给开发者。

在Backbone 1.0登陆的时候，Angelar.js也发布并逐渐流行开来。与Backbone聚焦在模型层不同，Angular.js更关注对视图层的改进。

Angular引入了编译模板以使HTML动态化的想法。它允许使用Directives向HTML元素注入行为。你可以将一个视图与一个模型绑定起来，当这个模型（数据）改变的时候，（与之绑定的）视图将自动更新。

Angular.js受欢迎程度的上升是因为它容易被引入任何项目，另外它也很容易上手。很多开发者被Angular.js吸引，因为它是由Google开发的，这给了它天生的“可靠”光环。

与此同时，Web组件规范承诺它将使开发者能够创建可重用的界面组件，这些组件与它们的上下文隔离，并能够方便地组合成其它组件。

Web组件规范由四个分离与互补的规范组成。

+ HTML 模板 （HTML Template） : 为组件提供HTML标记。
+ 自定义元素（Custom Element） : 提供了创建自定义HTML元素的机制。
+ Shadow DOM : 将组件的内部实现与渲染它的上下文隔离
+ HTML Import : 使得将Web组件引入一个(Web)页面成为可能

在Google的一个小组开发了一个polyfill（译者注：未找到这个词的很好翻译，直译的话是“垫片”。一种使旧的浏览器环境能够支持新的Web规范（主要是Javascript）的程序）库，为当时的所有浏览器都提供了对Web组件的支持。这个库被命名为Polymer，并在2013年开源。

Polymer是第一个使我们能通过组合组件来构造交互式(Web)应用的库。早期的使用者从这种组合能力中获益的同时也发现了很多应该由框架来解决的性能问题。

同时，一小组开发人员受Ruby on Rails的理念启发，计划创建一个“基于约定的、社区驱动的、用于构建大型Web应用的开源框架”

他们从SproutCore 2.0的一个分支开始，这是一个在模型、控制器、视图之间有良好分离的基于MVC的框架。这个新的框架被称为Ember.js。

开发“基于约定”的框架的第一个挑战就是找到大型Web应用的通用模式。Ember.js的开发团队到那些大型的Backbone应用中去寻找相似性。

他们发现了渲染嵌套视图的需求，这些嵌套视图中，应用的一部分保持不变，而另一些部分则不断变化。（译者注：感觉这段翻译的意思不是很到位，因此将原文附上：They identified the need to render nested views where some parts of the application were consistent while other parts changed from one part of the app to another.）

他们也发现URL在Web应用的架构中扮演了关键的角色。他们将嵌套视图的概念和URL的重要性结合创建了路由系统作为进入应用的入口点，同时控制了最初的视图渲染。

![](http://o9si8u3ts.bkt.clouddn.com/2017-07-15-1-rx9bWvoWTaEJSY8qAuuh4A-2.png)
(Elements of Ember.js — source Ember JS — An In-Depth Introduction)

在Ember.js核心团队的领到下，Embers社区与2013年8月发布了Ember.js 1.0。它提供了一个MVC架构、强壮的的路由系统，以及使用可编译模板的组件。和Angular.js、Plymer一样，Ember.js也严重依赖双向绑定来保持视图与状态的同步。

大约2014年年中的时候，一个新的库开始引起开发者的注意。Fackbook为他们的平台开发了一个框架，并且以React的名字对外发布。

在那个时候其它所有框架都依赖对象操作和属性绑定，React引入了将所有组件作为纯函数、以函数参数为组件属性的想法。

![](http://o9si8u3ts.bkt.clouddn.com/2017-07-15-1-sUeInQGMBhFVqW-rHj1JZg.png)
（组件是一个返回DOM的函数。[图片来源](https://facebook.github.io/react/docs/components-and-props.html#functional-and-class-components) ）

当一个属性的值发生变化，组件的渲染（render）函数将被调用并返回一个新的组件树。React将返回的组件树与一个虚拟的DOM树比较以决定如何更新真正的DOM。这个“重新渲染所有东西并将结果与虚拟DOM树比较”的技术被证明性能非常好。

![](http://o9si8u3ts.bkt.clouddn.com/2017-07-15-1-cV-klTo3DKl0Uo2Znk3V6g.png)

Angular.js的开发者遭遇到由Angular.js的变化检测机制引起的性能问题，Ember社区则对依赖双向绑定和“观测器(observer)”的大型应用带来的挑战有切身体会。

React做到了Polymer在当时未能实现的事情。React展示了组件架构也是能有好的性能的。React在性能基准上对Ember和Angular.js有压倒性优势。一些勇敢的Backbone开发者引入React作为应用的视图层来解决遇到的性能问题。

作为对React带来威胁的响应，Ember核心团队制定了一个将React的理念带入Ember框架的计划。他们意识到对向后兼容性的需要，因此制定了一个允许现存应用升级到包含新的渲染引擎的Ember版本的路径，这个渲染引擎受到了React的启发。

经过4次小版本发布以后，Ember.js放弃了视图层，将社区转向基于命令行的构建过程，并将基于组件的架构作为Ember应用开发的基础。这个逐步完成的对框架做出重大架构修改的过程称为“不停步的稳定性（Stability without Stagnation）”，这已成为Ember社区的基本信条。

在Ember向React学习的同时，React社区也采用了由Ember推广开来的路由技术。今天大型的React应用都采用了React Router，这是由router.js的一个分支发展而来的，后者向Ember提供了路由功能。

Ember引领并推广了使用命令行工具作为构建和发布Web应用的缺省界面，这是它对于现代Web应用的开发方法最大的贡献之一。

大约2015年年中的时候，Angular.js的核心团队得出结论，他们的框架已经进入了演化的死胡同。Google需要向它的开发者提供一个能够建造健壮的应用的工具，Angular.js无法满足这一要求。他们开始开发一个新的框架，它将成为Angular.js精神上的后继者。Angular.js的流行只得到了Google非常少的支持，与此不同的是，新的框架得到了Google的全力支持。Google在这个被称为Angular的后继产品中投入了30人以上的开发团队。

相比Angular.js而言，这个新框架涵盖的范围非常广。Angular团队将这个新框架称为一个“平台（platform）”，因为他们计划为专业的开发者提供开发Web应用所需要的所有东西。与Ember和React一样，Angular也使用基于组件的架构，但它是第一个使用TypeScript作为缺省编程语言的框架。

![](http://o9si8u3ts.bkt.clouddn.com/2017-07-15-1-c4T4WMmvhkQ4yc24dfzgMA.png)
（使用TypeScript开发的Angular组件）

TypeScript提供了类（classes），模块（modules）和接口（interfaces）。它支持可选的静态类型检查。对于从Java和C#转过来的开发者来说这是个完美的语言。TypeScript和Visual Studio Code一起提供了优秀的Intellisense支持。

![](http://o9si8u3ts.bkt.clouddn.com/2017-07-15-1-m6CUCh3LRpJNHV2axqtkAQ.png)
（Intellisense in Angular Apps — [来源](http://rafaelaudy.github.io/simple-angular-2-app/) ）

Angular是高度结构化的、基于约定的，同时依然提供了进行配置的功能。它有一个强大的路由系统。Angular团队正在努力工作，使得他们的新框架能提供Google的开发者期待专业的开发环境能提供的所有东西。他们对于完整性的关注将使整个Angular社区受惠。

2017年5月，Polymer  2.0 带着对绑定系统的改进来到人们面前，它减少了对“polyfills”的依赖，并和最新的Javascript标准保持一致。新版本引入突破性改变的同时也包含一个帮助用户升级至新版本的详细计划。新的Polymer包含一个命令行工具帮助构建和部署Polymer项目。

在2017年6月，所有顶级的框架都采用了基于组件的架构。每一个框架都提供路由作为将应用分隔为多个逻辑部分的方式。像Redux这样的状态管理技术被提供给所有的框架。React, Ember和Angular都允许为了SEO和初次访问而使用“服务器端渲染”，

所以你怎么知道该使用哪个工具来构建现代Web应用呢？我建议你审视一下你组织的人员构成再决定哪个框架最合适。

React作为一个库只是拼图中的一小块。React提供了一个轻薄的视图层，而让开发者自己去选择架构中的其它部分。没有什么是封闭在盒子中的，所以你的团队对于使用的每一样东西都有完全的控制权。如果你有一支熟悉函数式编程和不可变数据结构、有经验的Javascript开发团队，那么“一切自己选择”的风格是可行的。React社区在使用Web技术方面走在进化的最前沿。如果你的组织需要用同一套代码支持多个平台，掌握React将能使你用它开发Web应用，用React Native开发本地（移动）应用，用ReactVR为VR设备开发。

对于从Java和C#转过来的企业开发者，Angular是一个非常合适的平台。TypeScript和Intellisense支持将使得这些开发者感觉非常舒服。即使Angular很新，已经有了很多第三方组件库可以购买并马上投入使用。Angular团队承诺通过快速迭代不断改进框架而不会再次破坏向后兼容性。（译者注：Angular不兼容Angular.js。）Angular也能使用NativeScript来开发高性能的本地应用。

Ember.js是一个能优化小型团队和高技能个人开发者的生产率的框架。它对约定而非配置的关注为新的开发者和需要长期维护大型项目的组织提供了非常好的起步点。当最佳实践发生变化时，对于“不停步的稳定性”的承诺已被证明是一种维护大型应用而无需重写系统的有效方式。成熟、稳定，以及对创建共享的基础元件的投入创造了一个生态系统，使得大部分开发工作惊人的容易。如果你正在为一个长期项目选择一个可靠的框架，Ember是一个优秀的选择。

如果一个大型组织希望创建一个单一的风格指导和一系列能在整个组织中使用的组件，那么Polymer是一个非常好的框架。框架提供了和其它框架一样好的开发工具。如果你想在应用中使用一些先进特性又不想写大量Javascript代码，那么对你的组织来说Polymer是一个正确的工具。

我们正在学习为浏览器构建应用的方法，并且对一些好想法达成了共识。所有框架的构建者都很关心他们的用户。问题是哪个社区和生态系统对于你的组织和使用场景更加合适。

我希望这篇文章能帮助你了解现代Web生态系统的发展情况，并对你构建下一个现代Web应用有所帮助。

（转载请注明出处，并保留英文原文地址。）
