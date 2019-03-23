---
layout: post
title: Microservice 与 DDD
description: ""
category:
tags: []
---

{% include JB/setup %}

这篇算是对最近一年多时间学习和实践的总结。先放结论：

*TLDR: 一个微服务的合理粒度是包含属于同一个Bounded Context的一个或多个紧密关联的Aggregate。*

## 微服务

软件架构描述的是软件系统如何分割为组件、以及组件之间如何交互通信。软件系统的组件应该如何划分、组件的粒度多大合适，这是软件架构师永恒要考（纠）虑（结）的问题。

微服务是一种软件架构模式。因此如何将一个大的系统划分成多个微服务、每个微服务的粒度应该有多大也是微服务设计中最重要的问题。

从组件的角度看，每个微服务可以看成是一个或几个核心业务逻辑组件加上外围的基础设施组件组成。基础设施组件包括Service Endpoint、数据持久化等、事件发布等。

## Bounded Context 

Bounded Context 与下文的 Aggregate 都是 Domain Driven Design （[Eric Evans](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/ref=sr_1_1?keywords=domain+driven+design&qid=1553344486&s=gateway&sr=8-1)）中的重要概念。

一个大的问题域模型可以被划分成多个Bounded Context。每个Bounded Context 有自己的一套Ubiquitous Language。这里的Ubiquitous Language 我觉得可以理解为术语、行话。即使同样的概念在不同的Bounded Context中也可能有不用的名词（术语）来表示。

比较经常被举出的的Bounded Context的例子有CRM、仓库管理、订单处理等。

## Aggregate

Aggregate指一族紧密关联的对象，在修改的数据的时候，它们总是作为一个整体被看待。Aggregate划定了数据一致性规则的边界。

在DDD确定的原则中，Aggregate外部的对象只能应用Aggregate中的一个对象，这个对象被称为 Aggregate Root。一个事务应该只修改一个Aggregate的示例。因此Aggregate也定义了事务的边界。

## 简单的推理

即使不采用微服务，不属于同一个Bounded Context的Aggregate都不太可能在同一个monolithic系统中，更不用说属于同一个微服务了。

一个Aggregate显然能很好地满足SRP和CCP原则，一个Aggregate就能构成一个组件。

每个微服务都可能（可以、应该）有自己的数据库。如果一个Aggregate跨过了微服务的边界，就会出现一个跨微服务的事务的情况。虽然这也有处理的手段，但是会需要很多复杂的处理机制。因此，显然将Aggregate划定的事务边界容纳在单个微服务的边界内是最合理的。

如果有多个紧密结合的Aggregate，比如它们经常需要协同对外提供服务、有比较多的交互，那么将它们组合在同一个微服务中，虽然可能打破了一个微服务具备单一功能和职责的定义，但是也有存在的价值。特别是在系统开发的早期、Aggregate之间的划分与交互还常常会变化的时候，粒度比较粗一些的微服务会更有助于提高开发效率。这与早期组件划分宜粗不宜细的原则也是相容的。

## 更进一步的推论：

一个微服务的最小粒度是一个Aggregate，或者在采用CQRS的情况下C或Q中的一个。（关于CQRS可能在下一篇中涉及。）

## 参考资料

+ [领域驱动设计:软件核心复杂性应对之道](https://www.amazon.cn/dp/B01GZ6T12K/)
+ [实现领域驱动设计](https://www.amazon.cn/dp/B00IYTVWA6)
+ [架构整洁之道](https://www.amazon.cn/dp/B07HN66S4D)
+ [Aggregate Oriented Microservices](https://medium.com/@unmeshvjoshi/aggregate-oriented-microservices-d314eb04f2b1)
