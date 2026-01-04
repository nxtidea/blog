---
title: 在Mac上安装Photoshop
summary: 在优雅的 Mac 环境下，安装 Adobe Photoshop 竟没有那么容易。
date: 2025-01-25
tags: ["杂症笔记", "Mac"]
draft: false
slug: install-photoshop-on-mac  
---

## 最终步骤

### 寻找安装包

从微信搜索“Mac Photoshop”，会有公众号分享资源。我选用了[这一篇](https://mp.weixin.qq.com/s/usWskSJEGpmjGoBI6TB24w)。其他途径不太可靠。

### 安装要点

打开我的安装包，其中有用的只有两个文件夹`install` 和`patch`&#x20;

1. 进入`patch`文件夹，会有两个程序，先运行`anticc`。

2. 运行`install`文件夹，运行`install.app`程序。

3. 回到`patch`文件夹，运行剩下的一个破解程序。

这么做是因为，**Mac 上的 Photoshop 需要手动安装 Adobe Creative Cloud 作为支持才能正常安装。** 去官网安装完整版的 ACC 当然可以，这个 anticc 是去除了官方 ACC 中我们用不到的组件的精简版本。所以第一步需要从 ACC 和 anticc 二选一，然后再进行安装和打补丁。

## 报错与解决办法

### 已损坏错误

现象：直接运行`install.app` ，提示“xxx.app 已损坏，无法打开，你应该将它移到废纸篓”

原因：Mac 的安全限制。

办法：在终端输入`sudo xattr -r -d com.apple.quarantine + 空格 + 在应用程序中找到App拖入终端里面` ，详见[参考文章](https://www.shejibaozang.com/document/1850.html)

### 501 错误

现象：直接运行`install.app` ，提示“此时无法安装 Adobe Photoshop by xxx。（错误代码： 501）”

原因：缺少 ACC 环境。

办法：安装官方 ACC，或 anticc，安装后再运行即可。

参考：https://www.bilibili.com/opus/920092968187068436

### 打开程序是英文版

现象：虽然安装时选择了中文，但是打开程序还是英文界面且语言选择只有英文。

原因：不明。有可能是安装包的问题。

办法：手动打上中文补丁，我从[此处](https://macwk.cn/app/2145.html)下载。

## 阶段性总结

相比于 Windows，在 Mac 安装 Photoshop 多了两点麻烦：

1. 由于系统安全性，在运行安装程序时需要执行额外的命令。

2. 在 Mac 上，需要提前自行安装 ACC 环境，而 Windows 下面的安装包则会自动安装。

## 进一步探索

### 用于解决“安装包损坏”的命令是什么含义？

以下是 claude 的回答，我觉得很好：

> 这个现象涉及到 macOS 的安全机制，让我为你详细解释:
>
> 1. Gatekeeper 机制
>
> * macOS 有一个叫 Gatekeeper 的安全功能
>
> * 它会检查新下载的应用程序是否来自可信来源(苹果商店或认证开发者)
>
> * 对于不明来源的应用，系统会阻止运行并显示"已损坏"的提示
>
> 2. Quarantine 属性
>
> * 当从互联网下载文件时，系统会自动添加 quarantine 属性
>
> * 这个属性记录在文件的扩展属性(extended attribute)中
>
> * com.apple.quarantine 就是这个隔离标记
>
> 3. 解决方案原理
>
> 这个命令的作用是:
>
> * xattr: 管理文件扩展属性的工具
>
> * -r: 递归处理(包含所有子文件夹)
>
> * -d: 删除指定属性
>
> * com.apple.quarantine: 要删除的隔离属性
>
> 4. 为什么这样做有效
>
> * 删除 quarantine 属性后，Gatekeeper 就不会再对这个应用进行安全检查
>
> * 应用就可以正常启动了
>
> 需要注意的是，这种操作会绕过系统安全检查，建议只对可信任的来源应用使用。

### 错误 501 是什么意思？

同样有 claude 回答：501 是 Adobe 特有的错误，就是代表缺少 ACC 环境。

