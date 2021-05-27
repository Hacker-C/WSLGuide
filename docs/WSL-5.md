---
title: 玩转WSL(5)之zsh常用配置和插件
date: 2020-08-27 09:31:29
tags: WSL
categories: WSL
index_img: https://s3.ax1x.com/2021/02/14/ysagaT.jpg
---

# 前言

既然已经把 WSL+zsh 作为了我们的生产工具，那么就不免要对 zsh 做一些相关的配置并安装一些好用的插件，来提高我们的开发效率。

<!--more-->

# 1. zsh 常用配置

zsh 的配置文件在 `~/.zshrc` 位置，使用 `vim ~/.zshrc` 即可打开。
打开后我们主要可以看到有 `ZSH_THEME`、` plugins`、`alias` 等项，接下来一一介绍。

## 1.1 ZSH_THEME

`ZSH_THEME` 设置 oh-my-zsh 的主题。只需将其值改为对应的主题名即可。

```bash
# 查看当前zsh系统自带了哪些主题
ls ~/.oh-my-zsh/themes
# 查看当前主题
echo $ZSH_THEME
# 设置为随机主题
ZSH_THEME=random
# 设置为随机主题后，刷到了喜欢的主题，可通过以下命令查看当前主题：
echo $RANDOM_THEME
设置为在指定主题间切换
ZSH_THEME_RANDOM_CANDIDATES=( "robbyrussell" "agnoster" ）
```

> ❗ 注意：
> ① `ZSH_THEME` 和主题名之间没有空格！
> ② 每次切换主题要刷新一下缓存（`source ~/.zshrc`）或者重新打开终端
> ③ 但设置的主题出现字体样式乱码，则是字体问题。需要下载并安装适合命令行（font for powerline）或编程字体。（强烈推荐 Meslo Nerd Font）关于如何下载安装，请看这一篇：[WSL(2)](http://mphy.gitee.io/WSL-2) 的字体设置部分。

个人强烈推荐的是 [powerlevel10k](https://github.com/romkatv/powerlevel10k) 主题。
还能自由定制，响应速度极快。我的一些自制的预览效果如下，且内置了 100 多个主题。（关于安装和配置 powerlevel10k 主题后续文章将会更新...）
![p10k1](https://s1.ax1x.com/2020/09/02/w9ZaGt.png)
![p10k2](https://s1.ax1x.com/2020/09/02/w9ZdRP.png)
下面是官网的图。
![p10k3](https://s1.ax1x.com/2020/09/02/w9MfzR.png)

## 1.2 plugins

plugins 设置的是 zsh 插件。以下是推荐的一些插件，下载及安装在下文。（git 是 zsh 内置）

```bash
plugins=(git
         zsh-autosuggestions
         zsh-syntax-highlighting
)
```

## 1.3 alias

alias 配置指令的简写形式，极大提高开发效率。
配置 alias 的方法很简单，使用 `vim ~/.zshrc` 找到 `# Example alias` 这里，然后按照下面方式配置。
以下是我的一些 alias 配置。

```bash
alias cdd="cd /mnt/d"
alias cde="cd /mnt/e"
alias cdjn="cd /mnt/d/java_notes"
alias cddp="cd /mnt/e/desktop"
alias gpsom="git push origin master"
alias gplom="git pull origin master"
alias gl="git log"
alias ga="git add ."
alias gcm="git commit -m"
alias cl="clear"
alias neo="neofetch"
alias sz="source ~/.zshrc"
alias v="vim"
alias vr="vim README.md"
alias py="python3"
alias python="python3"
alias jc="javac"
alias j="java"
```

# 2. zsh 常用插件

> ✅ zsh 默认安装了很多插件，只要在 `~/.zshrc` 中开启即可。先介绍一些 zsh 没有的插件。

## 2.1 zsh-autosuggestions

根据历史使用指令的指令自动提示补全插件。下载安装方法：

1. 克隆 github 上该项目（默认在 ~/.oh-my-zsh/custom/plugins）

   ```bash
   git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
   ```

2. 将 `zsh-autosuggestions` 添加到 `~/.zshrc` 中

   ```bash
   plugins=(zsh-autosuggestions)
   ```

3. 重启 zsh 终端或新建一个 WSL 窗口
4. 修改指令提示的字体颜色（使其显示更明显）
   ```
   vim ~/.oh-my-zsh/custom/plugins/zsh-autosuggestions/zsh-autosuggestions.zsh
   ZSH_AUTOSUGGEST_HIGHLIGHT_STYLE='fg=cyan'
   ```

## 2.2 zsh-syntax-highlighting

zsh 指令语法高亮。下载安装：

1. Clone this repository in oh-my-zsh's plugins directory:
   ```bash
   git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
   ```
2. 配置 `~/。zshrc` 的 `plugins`
   ```
   plugins=( [plugins...] zsh-syntax-highlighting)
   ```
3. 重启 zsh

## 2.3 git-open

快速打开本地仓库关联的远程仓库（访问 github 远程库，超级方便）。
安装：

1. 克隆仓库
   ```bash
   git clone https://github.com/paulirish/git-open.git $ZSH_CUSTOM/plugins/git-open
   ```
2. 在 `~/.zshrc` 中配置

   ```bash
   plugins=( git-open )
   ```

3. 刷新配置
   ```bash
   source ~/.zshrc
   ```
4. 使用（在本地库的目录中）
   ```bash
   git open
   ```

## 2.4 bat

`bat` 替代 `cat` 指令，具有语法高亮、行号显示、文件目录显示清晰等强大功能。
官网：https://github.com/sharkdp/bat

> 安装方法暂未更新...

## 2.5 sublime

github 地址：[sublime plugin](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/sublime)

在 zsh 命令行打开 sublime text。

> 如果你习惯用 sublime text，就安装这个插件。如果你使用 `vs code` 则直接使用 `code test.md`，然后提示你安装一个 `VS Code Server for x64`。装好后就可以在 zsh 打开 vscode。

## 2.6 neofetch

显示系统信息和 logo。（就是看起来美观酷炫，实际上没啥用。）

1. 下载安装
   ```bash
   sudo add-apt-repository ppa:dawidd0811/neofetch
   sudo apt-get update
   sudo apt-get install neofetch
   ```
2. 使用
   输入指令 `neofetch` 即可使用。（这里我使用了 alias 简化命令 `neo`）
   ![neofetch](https://s1.ax1x.com/2020/08/27/dhlQgK.png)

> ✅ 下面是一些 zsh 安装了的插件。（需要手动配置在 `~/.zshrc` 中）

## 2.4 git

git 是 oh-my-zsh 默认开启的插件，提供了大量 git 的 alias。
查看详细 git alias：

```bash
vim ~/.oh-my-zsh/plugins/git/git.plugin.zsh
```

查看指定缩写指令（以 add 为例）：

```bash
alias | grep add
```

## 2.5 extract

功能强大的解压插件，所有类型的文件解压一个命令 `x` 全搞定。

```bash
plugins=( extract )
```

更多相关请关注：[WSL 专栏](http://mphy.gitee.io/categories/WSL)
