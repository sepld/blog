---
title: "以太坊私链(联盟链)环境搭建到Dapp部署(一)"
date: 2018-11-19T17:08:24+08:00
lastmod: 2018-11-19T04:29:09-08:00
draft: false
keywords: [geth]
description: "以太坊开发环境搭建"
tags: [以太坊, geth]
categories: [以太坊]
author: "sepld"
---

> 孤独中的快乐，淋漓正直，是灿烂中的忧伤，拥有一颗不肯面对世俗的灵魂，却是简单中的高贵

## 简介

关于以太坊是什么，就不从官网抄了，相信也不用在这重复。本文要做的很简单：**搭建环境，启动节点**

## 准备

- 平台 -- ubuntu18.04
- 客户端 -- geth
- 编译工具 -- go


### 安装Go
#### 步骤
可以直接在[官网下载](https://golang.org/dl/)对应版本，也可以直接[点击下载](https://dl.google.com/go/go1.11.2.linux-amd64.tar.gz)官方**linux**版本

在包含压缩包的目录执行下列命令，可将压缩包解压至默认目录 **/usr/local**下的go文件夹
```
tar -C /usr/local -xzf go$VERSION.$OS-$ARCH.tar.gz
```

添加环境变量，执行下列命令
```
vi ~/.profile     # 打开家目录下 .profile 文件
export PATH=$PATH:/usr/local/go/bin  # 在文件最下面添加此行，然后保存退出
source ~/.profile      # 更改文件使生效
```

检查安装， 直接输入go，可以看见一些go命令使用方法的输出。输入 go env 可以查看go环境变量设置

安装完成


### 安装geth

这里使用的是go版本客户端
#### 步骤
克隆仓库
```
git clone https://github.com/ethereum/go-ethereum.git
```

编译
```
cd go-ethereum
make geth  # 只编译geth
// or
make all   # 编译全套

```

安装已经完成，执行测试
```
geth console
```

直接输入geth会连接到以太坊主网并开启一个javaScript命令窗口并且日志也会在此窗口凑热闹，很闹心。
此命令开启后会直接同步以太坊主网区块，好多十个G啊, 几天也同步不完。
一般我们不会这么执行(除非自己跟自己闹别扭)。如果你有同感，那么恭喜你，安装成功。
```
geth --testnet console
```

此命令连接到以太坊测试网络，同样会同步一堆区块。

> 祝君安
