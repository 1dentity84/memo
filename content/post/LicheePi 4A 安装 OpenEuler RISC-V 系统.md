---
author: Joanna Wu
title: LicheePi 4A 安装 OpenEuler RISC-V 系统
date: 2024-09-04
description: 
math: false
---

## 一、准备工作

### 1.1.  下载 openEuler RISC-V 系统镜像

[镜像下载](https://mirror.iscas.ac.cn/openeuler-sig-riscv/openEuler-RISC-V/preview/openEuler-23.09-V1-riscv64/lpi4a/)

以 **LicheePi 4A 16G** 为例：按照 `README.lpi4a` 文件中的提示下载带图形界面的镜像：

+ `root-20231130-224942.ext4.zst`

+ `boot-20231130-224942.ext4.zst`
+ `u-boot-with-spl-lpi4a-16g.bin`

**下载完成后将 `zst` 压缩包解压为 `ext4` 格式** （使用的 [7Zip ZS](https://github.com/mcmilk/7-Zip-zstd/releases/tag/v22.01-v1.5.5-R3) 解压）

### 1.2. 下载烧录工具

在[网盘](https://pan.baidu.com/e/1xH56ZlewB6UOMlke5BrKWQ)中下载 `burn_tool.zip`, 解压后其中包括 win/linux/mac 三个系统下的 fastboot 烧录工具

## 二、准备烧录

### 2.1. Windows 下禁用数字签名

Windows 下烧录时，需要先进入高级启动模式，禁用数字签名，才能正常安装下面的驱动。

禁用数字签名步骤如下 （此处以 **Win 11** 为例）：

1. 设置 - 系统 - 恢复 - 高级启动 - 立即重新启动

![pic1](https://github.com/JoannaWu84/blog/blob/main/static/images/pic1.jpg?raw=true)

![pic2](https://github.com/JoannaWu84/blog/blob/main/static/images/pic2.jpg?raw=true)

2. 重启后，点击 疑难解答 - 高级选项 - 启动设置 - 重启

![pic3](https://github.com/JoannaWu84/blog/blob/main/static/images/pic3.jpg?raw=true)

![pic4](https://github.com/JoannaWu84/blog/blob/main/static/images/pic4.jpg?raw=true)

3. 按F7 选择“禁用驱动程序强制签名”，随即电脑自动重启

![pic5](https://github.com/JoannaWu84/blog/blob/main/static/images/pic5.jpg?raw=true)

### 2.2. Windows 下安装驱动

1. 按住板上的白色 `BOOT` 按键不放，用 USB-C 线将开发板和电脑连接起来，打开设备管理器出现 `USB download gadget` 设备，说明 LPi4A 设备已进入烧录模式

![pic6](https://github.com/JoannaWu84/blog/blob/main/static/images/pic6.jpg?raw=true)

2. 双击上图中的 `USB download gadget` ，点击 “更新驱动程序”

![pic7](https://github.com/JoannaWu84/blog/blob/main/static/images/pic7.jpg?raw=true)



3. 粘上驱动程序目录的路径

![pic8](https://github.com/JoannaWu84/blog/blob/main/static/images/pic8.jpg?raw=true)

![pic9](https://github.com/JoannaWu84/blog/blob/main/static/images/pic9.jpg?raw=true)

+ 到这里驱动就安装完成啦！

## 三、烧录镜像

### 3.1. 编辑 `burn_lpi4a.bat` 文件

+ 编辑 burn_tool.zip 文件夹里面的 `burn_lpi4a.bat` 文件，将镜像路径更改成实际使用的镜像及名称。 `fastboot.exe` 的路径也需要修改。

**修改前：**

![pic10](https://github.com/JoannaWu84/blog/blob/main/static/images/pic10.jpg?raw=true)



**修改后如下：**

![pic11](https://github.com/JoannaWu84/blog/blob/main/static/images/pic11.jpg?raw=true)

### 3.2. 启动烧录程序

+ 双击运行 `burn_lpi4a.bat` 开始烧录，出现如下界面证明烧录成功啦！

![pic12](https://github.com/JoannaWu84/blog/blob/main/static/images/pic12.jpg?raw=true)

##  四、登录OpenEuler RISC-V

- 用户名: `openEuler`
- 默认密码: `openEuler12#$`
- 执行 neofetch 命令

![pic13](https://github.com/JoannaWu84/blog/blob/main/static/images/pic13.jpg?raw=true)

#### **注意事项：**

1. 开发板连接电脑时，需长按 BOOT 键，再插入 usb-c

2. 编辑 `burn_lpi4a.bat` 文件时，也需要修改 `fastboot` 文件的路径 （需仔细）

3. 双击 bat 文件烧录镜像遇到了问题，无法执行。长按 BOOT 键重连接 C 口，执行bat文件正常运行。

