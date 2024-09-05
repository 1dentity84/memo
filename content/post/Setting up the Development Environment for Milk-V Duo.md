---
author: Joanna Wu
title: Milk-V Duo 开发环境搭建——以 Ubuntu 22.04 为例
date: 2023-10-26
description: 
math: false
---

**准备编译环境**

+ Ubuntu 22.04 LTS

## 1.安装编译依赖的工具

```markdown
sudo apt install pkg-config build-essential ninja-build automake autoconf libtool wget curl git gcc libssl-dev bc slib squashfs-tools android-sdk-libsparse-utils jq python3-distutils scons parallel tree python3-dev python3-pip device-tree-compiler ssh cpio fakeroot libncurses5 flex bison libncurses5-dev genext2fs rsync unzip dosfstools mtools tcl openssh-client cmake
```

## 2.安装补充依赖libssl1.1

SDK 中的 mkimage 命令依赖的 libssl1.1，Ubuntu 22.04 缺失，需要手动安装

```markdown
wget http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl1.1_1.1.1-1ubuntu2.1~18.04.23_amd64.deb
sudo dpkg -i libssl1.1_1.1.1-1ubuntu2.1~18.04.23_amd64.deb
```

## 3.获取SDK

```markdown
git clone https://github.com/milkv-duo/duo-buildroot-sdk.git
```

## 4.开始编译

```markdown
cd duo-buildroot-sdk/
./build_milkv.sh
```

第一次编译会自动下载所需的工具链，大小为840M左右，下载完会自动解压到SDK目录下的 `host-tools` 目录。

## 5.编译成功

```markdown
gnimage for milkv-duo success!
~/duo-buildroot-sdk/build
~/duo-buildroot-sdk
~/duo-buildroot-sdk/out ~/duo-buildroot-sdk
~/duo-buildroot-sdk
Gen image successful: out/milkv-duo-20230906-1547.img
```

**生成的固件位置**: `Home / duo-buildroot-sdk / out / milkv-duo-20230906-1547.img` （如下图所示）

![pic14](https://raw.githubusercontent.com/1dentity84/memo/main/static/images/pic14.jpg)

## 6.SD卡烧录

+ Windows下使用 `balenaEtcher` 烧录刚刚编译好的img

![pic15](https://raw.githubusercontent.com/1dentity84/memo/main/static/images/pic15.jpg)

## 7. SSH Milk-V Duo

+ 将SD卡插入Milkv的SD卡座，通过Type-C数据线与电脑连接。此时蓝灯开始闪烁，说明Milkv运行linux固件正常
+ [更新驱动参考此教程](https://gitee.com/joannawu/memo/blob/master/Milk-V%20Duo%20%E7%82%B9%E7%81%AF.md#3-ssh-milk-v-duo)

- 远程链接Milk-V Duo

   ssh root**@192**.168.42.1 默认密码：milkv
   
   

[**视频教程**](https://www.bilibili.com/video/BV1fG411k7yE/?)