---
title: 玩转WSL(8)之 配置编程环境
date: 2020-09-14 09:21:55
tags: WSL
categories: WSL
index_img: https://s3.ax1x.com/2021/02/14/ysagaT.jpg
---

# 前言

在 Windows 图形化或者 cmd 下配置编程环境实在是太麻烦了，遇到各种坑，比如网络错误、环境变量的配置等等。。而在 WSL 下配置，只需要几条命令就可以解决。本文给出了 Java，Python，C/C++ 编程环境配置方法。

<!--more-->

# 1. 配置 Java(JDK) 编程环境

安装命令：

```bash
sudo apt install openjdk-8-jdk
```

> 若这里遇到网络问题而中断，请一定要多尝试几次！

编译运行：

```bash
javac test.java
java Test
```

# 2. 配置 Python 编程环境

## 2.1 安装环境

WSL(Ubuntu) 默认安装了 python3，输入以下命令查看

```bash
python3 --version
```

若要更新至最新版本的 python3(wsl)，则输入：

```bash
sudo apt update && sudo apt upgrade  #升级wsl-Ubuntu
sudo apt upgrade python3  #更新python3
```

安装 python 的包管理器 pip：

```bash
sudo apt install python3-pip
pip3 --version  #查看是否成功安装
```

安装 venv

```bash
sudo apt install python3-venv
```

## 2.2 解释执行

```bash
python3 test.py
```

> 参考链接
> https://docs.microsoft.com/zh-cn/windows/python/web-frameworks#set-up-your-development-environment

# 3. 配置 C/C++(gcc/g++) 编程环境

## 3.1 配置环境

配置 C(gcc)：

```bash
sudo apt install gcc-8
```

配置 C++(g++)：

```bash
sudo apt install g++-8
```

安装位置：

```bash
cd /usr/bin
```

## 3.2 编译运行

> 实际上从编辑到运行经过了预处理、编译、汇编和链接等步骤，但开发者只关心运行结果。因此编译器（gcc/g++）对此需求做了支持，在这里我把这些过程统称为编译。

**1. 分步执行**

1.1 生成可执行文件

```bash
gcc test1.c  # c语言
g++ test2.cpp   # c++
```

默认会生成一个 `a.out` 的文件。
1.2 执行文件输出

```bash
./a.out  #  c/c++
```

**2. 编译为指定文件**

2.1 编译生成指定文件

```bash
gcc test1.c -o test1.exe  # c语言
g++ test2.cpp -o test2.exe  # c++
```

生成了 `test1.exe` / `test2.exe` 文件。
2.2 执行文件输出

```bash
./test1.exe  # c语言
./test2.exe  # c++
```

**3. 一步执行**

```bash
gcc test1.c && ./a.out  # c语言
g++ test1.cpp && ./a.out  # c++
```

> 参考链接
> http://c.biancheng.net/view/7959.html

更多相关请关注：[WSL 专栏](http://mphy.gitee.io/categories/WSL)
