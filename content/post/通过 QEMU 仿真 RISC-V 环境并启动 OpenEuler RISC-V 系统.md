---
author: Joanna Wu
title: 通过 QEMU 仿真 RISC-V 环境并启动 OpenEuler RISC-V 系统
date: 2023-04-13
description: 
math: false
---

## 安装ubuntu虚拟机以及支持 RISC-V 架构的 QEMU 模拟器
* 安装Ubuntu虚拟机，终端中通过指令安装qume模拟器：`$ sudo apt install qemu-system-misc`
* 安装依赖文件：`$ sudo apt install build-essential git libglib2.0-dev libfdt-dev libpixman-1-dev zlib1g-dev ninja-build`
* 创建 /usr/local 下的目标目录：`$ sudo mkdir -p /usr/local/bin/qemu-riscv64`
* 下载最新的 QEMU 源码包 (修订时为 7.0.0 版本)：`$ wget https://download.qemu.org/qemu-7.0.0.tar.xz`
* 解压源码包并切换目录：`$ tar xvJf qemu-7.0.0.tar.xz && cd qemu-7.0.0`
* 配置编译选项：`$ sudo ./configure --target-list=riscv64-softmmu,riscv64-linux-user --prefix=/usr/local/bin/qemu-riscv64`
* 编译安装：`$ sudo make && sudo make install`
执行命令：`$ qemu-system-riscv64 --version` （输出版本信:息QEMU emulator version 7.0.0）
## 下载 openEuler RISC-V 系统镜像
* 下载说明: 至少应当下载启动 payload (`fw_payload_oe_qemuvirt.elf`)，GUI 和 headless 中一种镜像和对应的启动脚本
* 下载目录: openEuler-RISC-V/testing/DATE/VER/QEMU/
* 内容说明：
    * `fw_payload_oe_qemuvirt.elf`: 利用 openSBI 将 kernel-5.10 的 image 作为 payload 所制作的 QEMU 启动所需文件
    * `openeuler-qemu-xfce.raw.tar.zst`: openEuler RISC-V QEMU GUI 镜像压缩包
    * `start_vm_xfce.sh`: GUI 虚拟机启动脚本
    * `openeuler-qemu.raw.tar.zst`: openEuler RISC-V QEMU headless 镜像压缩包
    * `start_vm.sh`: headless 虚拟机启动脚本
##  启动 openEuler RISC-V 虚拟机
* 解压镜像压缩包 `$ tar -I 'zstdmt' -xvf ./openeuler-qemu.raw.tar.zst`
* 执行启动脚本 `$ bash start_vm.sh`
## 登录虚拟机
* 用户名: `root`;

* 默认密码: `openEuler12#$`

* 执行neofetch命令

  ![neofetch](https://github.com/1dentity84/memo/blob/main/static/images/neofetch.jpg?raw=true)

>**若系统中neofetch丢失，通过以下命令安装neofetch**
>
>>`git clone https://github.com/dylanaraps/neofetch`
>>`cd neofetch`
>>`make install`

