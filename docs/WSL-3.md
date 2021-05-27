---
title: 玩转WSL(3)之 安装配置 oh my zsh
date: 2020-03-03 16:50:52
tags: WSL
index_img: https://s3.ax1x.com/2021/02/14/ysagaT.jpg
categories: WSL
---

# 0. 前言

WSL(Ubuntu) 默认终端是 bash， zsh 功能比 bash 要强大得多，但是配置起来太难了。国外的一个程序员看不下去一直这么单调的 zsh，就开发了 oh my zsh。配置起来，不要太简单。可谓是高档大气上档次，狂拽炫酷吊炸天。

<!--more-->

# 1. 安装 zsh

① 查看当前系统的 shell

```bash
echo $SHELL
```

② 查看系统安装的 shell

```bash
cat /etc/shells
```

③ 安装 zsh
若有 zsh，则切换未 zsh

```bash
chsh -s/bin/zsh
```

WSL(Ubuntu) 默认是未安装 zsh 的，使用以下指令安装并切换:

```bash
sudo apt-get install zsh
chsh -s /bin/zsh
```

④ 更新 zsh(oh-my-zsh)

```bash
omz update
```

# 2. 安装 oh my zsh

使用以下指令下载并安装 oh my zsh

```bash
sudo apt install zsh
sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
```

❌ 注意：若有人在这里遇到错误：`curl: (7) Failed to connect to raw.githubusercontent.com port 443: Connection refused` ，那是因为 github 被墙了。解决方法如下（亲测有效）:
输入网址(先确能进 github):https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh
进入后是一个文件，将该 `.zsh` 文件下载下来，保存为 `install.zsh`到一个目录。接下来在 WSL 进入该目录，执行命令：

```bash
chmod +x install.sh
./install.sh
```

完美解决！
![avatar](https://s1.ax1x.com/2020/08/26/dWyVKJ.png)

# 3. 切换主题

输入以下指令，进入 `.zshrc` 配置文件。

```bash
vim ~/.zshrc
```

> ❗ WSL(Ubuntu) 默认安装了 vim，其他若未安装则使用指令 `sudo apt-get install vim` 安装或使用 `vi` 进行编辑。

进入 `.zshrc` 后修改 `ZSH_THEME` 为指定主题。然后退出，记得使用 `source ~/.zshrc` 更新一下缓存。

> ❌ 注意：`ZSH_THEME=`与主题名之间没有空格！！！

推荐一些个人觉得好看的主题：robbyrussell,agnoster,muse,af-magic",rkj-repos

查看 oh my zsh 自带了哪些主题:

```bash
ls ~/.oh-my-zsh/themes
```

查看当前主题：

```bash
echo $ZSH_THEME
```

设置为随机主题：`ZSH_THEME=random` 后，刷到了喜欢的主题，可通过一下命令查看当前主题：

```bash
echo $RANDOM_THEME
```

设置为在指定主题间切换：

```bash
ZSH_THEME_RANDOM_CANDIDATES=( "robbyrussell" "agnoster" )
```

更多相关请关注：[WSL 专栏](http://mphy.gitee.io/categories/WSL/)
