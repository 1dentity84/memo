---
author: Joanna Wu
title: openEuler RISC-V上运行WPS
date: 2024-09-10
description: 
math: false
---

## 背景

+ **板子**：LicheePi 4A

+ **系统**：openEuler 23.09 riscv64

+ [视频教程](https://www.bilibili.com/video/BV1hGpxegEtn)

  

## 一、构建 box64

1. 克隆 box64 仓库

```markdown
git clone https://github.com/ptitSeb/box64
```

2. 生成编译配置文件

```markdown
cd box64
mkdir build; cd build; cmake .. ${OPTIONS}
```

这里用的是 RISC-V OPTION，替换为 `-D RV64=1 -D CMAKE_BUILD_TYPE=RelWithDebInfo`

3. 开始编译

```markdown
make -j4
```

4. 安装编译好的 box64

```markdown
sudo make install
```

## 二、运行WPS

1. 解压 WPS 安装包

```markdown
su
cd /var/opt
unzip /home/openeuler/
```

2. 用 box64 运行 WPS

**此处以运行 WPS Presentation 为例**

```markdown
cd /kingsoft/wps-office/office6
box64 wpp
```

![pic16](https://raw.githubusercontent.com/1dentity84/memo/main/static/images/pic16.jpg)

![pic17](https://raw.githubusercontent.com/1dentity84/memo/main/static/images/pic17.jpg)

### 相关文档：

box64 编译参考文档: https://github.com/ptitSeb/box64/blob/main/docs/COMPILE.md

WSP 安装包下载: https://www.wps.cn/product/wpslinux