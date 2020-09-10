---
title: 玩转WSL(1)之安装wsl
date: 2020-02-21 11:47:13
tags: WSL
categories: WSL
---

{% cq %}  初识并安装WSL {% endcq %}

<!--more-->

## 1.什么是 WSL

 WSL 全称是 Windows Subsystem for Linux ，顾名思义，WSL 就是  Windows 下的 Linux 子系统

## 2.WSL 的特性

+ 在 Microsoft Store 中选择你偏好的 GNU/Linux 分发版。
+ 适用于 Windows 的 Linux 子系统可让开发人员按原样运行 GNU/Linux 环境，包括大多数命令行工具、实用工具和应用程序，且不会产生虚拟机开销。
+ 使用类似于 Unix 的命令行 shell 调用 Windows 应用程序。
+ 在 Windows 上调用 GNU/Linux 应用程序。
+ 通过 bash 命令快速获得一个 ubuntu linux 环境，让你可以随时在 win10 下体验 linux ，启动快，比虚拟机还好用
+ 依附于 Windows 系统，所以其功能会受到限制

## 3. 安装 WSL

### 3.1 前提
WSL只支持 `Windows10` ，如果要继续使用，请先更新系统
### 3.2 安装
① 首先我们要启动 `Windows Subsystem for Linux` 这个功能
+ 以**管理员身份**打开 `Windows PowerShell` ，输入下面的指令
```js
Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux
```
+ 指令完成后，重启电脑

② 去 `Microsoft Store` 下载并安装 `Linux` 发行版，这里以 `Ubuntu` 为例。去商店安装的 `Linux` 发行版只能安装在C盘
+ 安装完以后点开 `Ubuntu`，按照提示输入用户名和密码，注意用户名不支持大写
+ 最后显示 `Installation successful!` 就说明安装成功！整个过程挺简单的，毕竟是 `Windows` 的子系统，对 `Windows` 用户很友好。

③ 现在，你可以开始在 `Windows` 下的 `Linux` 之旅了！

## 4.参考链接

[Microsoft MSL docs](https://docs.microsoft.com/zh-cn/windows/wsl/install-win10#troubleshooting)
[Windows Subsystem Linux Installation Guide For Windows 10](https://docs.microsoft.com/en-us/windows/wsl/install-win10)

更多相关请关注：[WSL专栏](http://mphy.gitee.io/categories/WSL/)

**❗ 法律声明**

> 本文作者：[Murphy Chen](https://www.zhihu.com/people/ai-xiao-xi-19)
> 本文链接：http://mphy.gitee.io/WSL-1（转载注明源链接）
> 版权声明：本博客作品除特别声明外，均为原创，遵循 **署名-非商业性使用-禁止演绎 4.0 未本地化版本 [CC BY-NC-ND 4.0](https://creativecommons.org/licenses/by-nc-nd/4.0/)** 协议发布
