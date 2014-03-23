---
layout: post
title: Android, GO!
categories: [技术]
tags: [android]
---

Android 的 Dalvik 虚拟机运行的不是 Java 程序，可以说 Dalvik 完全可以运行其它语言开发的程序，但是 Google 为了吸引 Java 程序员，允许 程序员使用 Android 的SDK 将 Java 代码转换成 Dalvik 可以运行的代码。它是如何实现的呢？Google 在开发 Android 的时候，雇佣了 Sun 的一些程序员，利用 Harmony 中的开源 Java 库来实现 Java 程序的转换，避开了授权费用。这意味着开发者可以使用 Java 语言为非 Java 平台开发程序，Android 的火爆发展不能给 Sun 带来商业利益，而且可能造成平台分裂。

开源领袖Ricard Stallman 早就指出Java 是“带着镣铐的自由”（Free but shackled），警告开发者谨防 Java 陷阱。此后，Sun 开源了大部分的 Java 实现代码，因此 Java 陷阱已经可以避免，但仍然要注意使用完全自由的平台，因为并非所有的平台都是自由的。 

如果 Google 收购 Sun，将 Java 收归己有，或者当初与 Sun 达成协议，也许今天情形会不同。或着当初开发 Android 的时候，Google 应该培育自己的 Go 语言，而不是急于利用现有的 Java 开发者队伍。Java 关于开放的说法只是一个假象，而如今 Java 易手，一切都改变了。 

很难想象 Google 会放弃 Android 系统，问题是如何发展它。Java 将逐步脱离开源社区，沦为 Oracle 的生财之道，这是一个利益当头、注重企业而不考虑个人开发者的公司，与 Java 的纠缠不清只能带来更多的麻烦。

现有的智能手机平台中，Java 已经不是开发者的首选，iOS，MeeGo 都有自己的开发环境，WebOS 不需要 Java 实现，而 RIM 也在逐渐抛弃 Java，转向 Adobe AIR，这意味着 Java 在手机市场的空间在逐步缩小。讽刺的是，现在 Android 的飞速发展反而有利于 Java 语言在手持领域的地位。如果 Google 抛弃 Java，是否 Java 将只能在低端机之间苟延残喘，逐渐消亡呢？相信随着 Web 开发技术的进步，HTML/CSS/Javascript这样的网络开发环境将成为网络应用的首选，而底层应用开发将会是 C/C++的天下。 