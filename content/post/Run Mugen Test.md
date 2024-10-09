---
author: Joanna Wu
title: Run Mugen Test
date: 2024-10-08
description: 
math: false
---

## 1.下载测试工具并安装

https://gitee.com/openeuler/mugen

+ ``git clone https://gitee.com/openeuler/mugen.git``
+ ``bash dep_install.sh``

## 2.设置测试环境

- ``cd mugen``
- `bash mugen.sh -c --ip $ip --password $passwd --user $user --port $port`

$ip   $passwd  $user   $port  按照实际参数填写替换

e.g.: bash mugen.sh -c --ip 192.168.2.54 --password 00000000 --user root --port 22


- 参数
  - 目标计算机的 IP 地址
  - 目标计算机的用户名，默认为 root
  - 密码
  - 目标计算机的 ssh 端口，默认为 22

## 3.运行测试

切换至root用户

运行所有测试用例：` bash mugen.sh -a`

运行一个测试套:  `bash mugen.sh -f testsuite`

运行一个测试用例:  `bash mugen.sh -f testsuite -r testcase`

运行完自动保存测试log

e.g.:  

bash mugen.sh -f NetworkManager

bash mugen.sh -f NetworkManager -r oe_test_service_nm-cloud-setup  

运行完成后查看测试日志

