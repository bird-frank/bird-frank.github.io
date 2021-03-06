---
layout: post
title: 《架构整洁之道》读书笔记（一）
description: ""
category:
tags: []
---

{% include JB/setup %}

## 序
《架构整洁之道》，英文原名《Clean Architecture》，作者Robert. C. Marin（Uncle Bob）。中国亚马逊上该书英文版亦被冠名为《软件架构与设计匠艺》。

《Clean Architecture》是作者“Clean”系列中的一本，另两本是《Clean Code》和《Clean Coder》。

## 架构设计的目标

作者提出应该使用软件开发所耗费的精力（effort）来度量软件设计的质量。软件架构的目标就是：使用最少的人力资源来创建和维护所需要的软件。

在这里作者没有使用“cost”（成本），而是用了“effort”一词。我的理解是，effort所涵盖的面比cost要广。虽然所有投入软件开发的有形资源最终都可以使用货币成本来度量，但还是有些无形资源是无法用金钱来度量的。比如软件企业和软件开发者的声誉、软件开发团队的士气、项目参与者的健康和家庭幸福……

更容易、更快速地进行变更的能力；意味着更少的缺陷；最小化的精力投入；最大化的功能和灵活性；这些都意味着更少的人力资源投入，从而等于更好的软件质量。

更好的质量意味着更低的成本；更低的成本就是更好的质量的体现。

> The only way to go fast, is to go well.（走的快的唯一途径就是走得稳。或者：欲速则不达。）

> Making messes SLOWER than staying clean. 

## 软件的价值
软件的价值从两个方面体现出来。一个是软件的行为，另一个是软件的结构。

软件的行为表现在控制机器满足用户的需求，而最重要的两个需求就是“挣钱”和“省钱”。开发者一般使用“功能规格说明书”或者“需求文档”来记录用户对软件行为方面的需求。

软件在结构方面——也就是软件架构——的价值体现在更容易地改变机器的行为。这也是软件一词中“软”的含义所在。

那么行为方面的价值和结构方面的价值哪个更重要呢？凭直觉来说，应该是满足客户的功能性需求更重要。但实际并非如此。

一个能满足功能性需求、但是很难变化的系统，意味着当需求发生变化时，需要非常大的投入才能实现新的、或者变化过的功能。极端情况下可能很快在新需求面前变得无用。

而一个虽然还没有完全满足功能性需求，但是很灵活、很容易修改的系统，并不需要很多投入就可以使其变得满足客户的需要。

因此，当我们面对的是需求随时可能变化的环境时，设计一个好的软件架构、使系统更加灵活、易于修改，便比只满足当前的功能性需求更重要。

那么需求有没有可能不变呢？曾经有不少人试图控制软件需求变更，例如通过大量的前期评审尽可能减少后期的需求变更，但现在的软件开发者已经认识到，需求变更非但是不可避免的，能够迅速修改系统行为应对外部环境变化提出的变更需求才是“软”件系统的价值所在。

软件结构方面的问题虽然很重要，但一般是不紧急的；而功能方面的需求可能重要也可能不重要，但常常显得很紧急。因此掌握这两方面的平衡便是软件开发者——特别是架构师——的责任。

设计一个好的软件架构是架构师的职责。相对于软件的功能特性来说，架构师要更加专注于软件的结构，并且在必要的时候还需要“Fight”，要勇于“捍卫”好的软件结构的设计，避免来自各方面的要求匆忙实现软件功能的压力。

## 总结
以上是本书“介绍”部分的主要内容。本书的主要内容就是讲解如何设计一个“好的”，也就是能投入最少的精力实现客户需求的软件架构，从而构建一个更容易变化、更少缺陷、更多功能和灵活性的软件系统。





