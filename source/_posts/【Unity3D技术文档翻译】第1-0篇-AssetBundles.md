---
title: 【Unity3D技术文档翻译】第1.0篇 AssetBundles
date: 2017-08-08 11:32:29
tags:
- unity3d
- unity3d翻译
categories:
- Unity3D
- AssetBundles
---

# 前言

“Unity圣典”是目前对官方文档翻译比较详细的，然而文档的最新更新日期是2013年，已经远远落后最新版本，参考意义有限。官方文档、脚本手册是学习Unity3D最直接有效的途径，然而一直没有中文版本，给很多开发人员带来了不便。因此我想在学习Unity3D的同时，将官方文档一道翻译。方便自己查看，同时还能方便其他后来的开发人员，何乐而不为？初次翻译，难免有错漏，欢迎指正！

PS：

1. 技术术语不会翻译，因为保持英文更加方便沟通和理解，必要时会同时给出中文翻译。

2. 翻译会更注重意译，而不是直译。

3. 从 AssetBundles 开始翻译是因为正好看到这里 ^_^。

4. 标题中的“第1.0篇”是为了表示出章节的从属关系，比如下一篇“AssetBundle 工作流”会是“第1.1篇”。

# 正文

本章原文所在章节：【Working in Unity】→【Advanced Development】→【AssetBundles】

# AssetBundles

一个 AssetBundle 就是一个会在运行时被加载的归档文件，它包含了和平台相关的特定资源（例如：Models、Textures、Prefabs、Audio clips，甚至可以是所有的 Scenes）。AssetBundles 相互之间可以具有“依赖性”，例如：AssetBundle A 中的 一个材质（material）可以引用 AssetBundle B 中的一个纹理（texture）。

为了能够在网络上更有效率地递送，AssetBundles 可以根据实际需要，选择引擎内置的算法进行压缩（LZMA算法和 LZ4算法）。

AssetBundles 可用于：可下载的内容更新（DLC）、降低初始安装包大小、针对用户平台进行最优化资源加载，以及降低运行时的内存压力。

# AssetBundle 里有什么？

好问题，事实上 AssetBundle 涉及了两个不同但是相关的事物。

首先，AssetBundle 可以指存储在磁盘上的实际文件。我们称这种文件为“AssetBundle 归档”，在本教程中，我们直接简称为“归档”。归档可以看作是一个容器，就像一个文件夹一样，里面保存了额外的一些文件。这些额外的文件由两种类型组成：序列化文件和资源文件。

其中，“序列化文件”是指：用你的资产组合形成各个对象，然后将它们写入磁盘中的一个文件，这个文件就是序列化文件。而“资源文件”就是一个个二进制数据块，这些数据块分别存储了特定类型的资产（比如：纹理和音频），这可以让我们在另一个线程上更有效地从磁盘中加载它们。

其次，AssetBundle 可以指一个实际的 AssetBundle 对象。你可以通过代码操控它，从一个特定的归档中加载你想要的一些资产。AssetBundle 对象包含了一组映射，即：“你添加到归档中的所有资产的文件路径”，以及“与这些资产相对应的对象们“，这两者之间的映射。你可以利用这种映射，在需要时加载你想要的对象。

题外话：

最后两段好难翻译，中英文思维方式完全不同。严重怀疑就算是外国人，看母语版的官方文档也要思考好一阵，而且还要有Unity基础才能看得懂。就拿最后一句话来说，原文是：

This object contains a map of all the file paths of the assets you added to this archive to the objects that belong to that asset that need to be loaded when you ask for it.
没错，就是这么绕这么长。头几遍完全看晕了，不反复琢磨个几十遍，结合自身已经有的认知，都理不清它到底想表达什么。我自己对这句话的翻译还算满意，不知道正在看这篇文章的人有没有看懂，泪目 T_T

如果本文对你有帮助的话，点个赞或者评论一下吧，让我知道有人来看过。
