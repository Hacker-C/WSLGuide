---
title: 玩转WSL(6)之配置Git
date: 2020-08-27 11:09:19
tags: WSL
categories: WSL
index_img: https://s3.ax1x.com/2021/02/14/ysagaT.jpg
---

本文适合 WSL(Ubuntu)。WSL(Ubuntu) 已经自带了 Git，并且我们可以配置 git alias(git 别名) 来简化 git 命令。WSL Git 公钥的生成和配置和 Windows 不同，本文主要涉及在 WSL 上更新 Git，并配置与 GitHub 连接的 SSH 密钥。

<!--more-->

> Tip:<font color=red>由于众所周知的网络原因，下载速度可能会很慢，如果不走代理的话，就耐心等。如果下载中断，那就多试几次。</font>

# 1. 更新 Git

查看 Git 版本

```
git --version
```

将 Git 更新至适合 WSL 的最新稳定版本

```
sudo apt-get install git
```

> 注意：若未安装 Git for Win，则可能需要安装。

# 2. 配置 Git 用户信息

设置用户名(Github ID)

```
git config --global user.name "your_name"
```

设置邮箱(Github email)

```
git config --global user.email <your_email>
```

# 3. 生成并配置密钥/公钥

- 在 WSL 下生成 SSH 公钥—私钥对（将邮箱替换为你的邮箱），此时生成的 SSH 密钥默认位于 `~/.ssh` 路径下，公钥为 `id_rsa.pub`，私钥为 `id_rsa`

```
# 执行完后只需一路回车即可
ssh-keygen -t rsa -b 4096 -C "your_email"
```

- 打开 ssh-agent 使之在后台运行

```
eval "$(ssh-agent -s)"
```

- 将私钥添加到 ssh-agent 之中

```
ssh-add ~/.ssh/id_rsa
```

- 查看并复制公钥

```
cat ~/.ssh/id_rsa.pub
```

- 将复制的公钥信息添加到 Github/Gitee

# 4. 配置 Git alias

编辑 `~/.gitconfig`，根据需要添加以下内容：

```
[alias]
    g = git
    a = add
    st = status
    cm = commit
    cl = clone
    ps = push
    pl = pull
    co = chekout
    br = branch
```

配置完后，就可以使用简化的 git 命令了。例如 `g a .` 表示 `git add .`

# 5. 参考链接

[MCS-WSL-Git](https://docs.microsoft.com/zh-cn/windows/wsl/tutorials/wsl-git#git-config-file-setup)
[掘金-LeoMalik-为 win10 打造原生 Linux 终端：使用 WSL 作为 Windows 下的主力开发工具](https://juejin.im/post/6844904064535248909#heading-9)

更多相关请关注：[WSL 专栏](http://mphy.gitee.io/categories/WSL/)
