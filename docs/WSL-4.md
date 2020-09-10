---
title: 玩转WSL(4)之vim常用命令和基本配置
date: 2020-08-24 15:26:49
tags: WSL
categories: WSL
---
# 前言
既然已经使用了命令行 WSL 进行编程开发了，那么就免不了要认识一下 Vim 这个命令行编辑器了。况且之前以及后面我们都要对 `~/.zshrc`(zsh配置文件)、`~/.vimrc`(vim配置文件)、`~/.p10k.zsh`(powerlevel10k主题配置文件)等进行编辑，所以而为了更好的配置基础开发环境，也需要学会 vim。
<!--more-->
# 1. 安装vim

WSL(Ubuntu) 默认内置 vim。其他 WSL 版本若未安装则使用指令 `sudo apt-get install vim` 安装即可。

# 2. vim三大模式及常用指令

> 只介绍常用指令，跟全面的可以在网上搜索到。

## 2.1 命令模式

使用 vim 刚进入要编辑的文件时，就处于命令模式。若处于其他模式，则使用 `Esc` 进入命令模式。
在此模式下：
① 按 `i`(insert) 进入输入模式，键盘输入内容；
② 按 `u`撤回上次修改，已经保存并且退出vim的则不能再撤回；
③ 按 `v`(visual)进入可视模式，从当前光标位置移动到目标位的内容置，使用 `y`(copy)复制这段内容，使用 `p`(paste)粘贴；
④ 按 `J`(大写)合并光标所在行和下一行内容；
⑤ 按 `x` 删除当前光标所在位置的字符；
⑥ `dd`，删除当前光标所在行的内容；
⑦ `ndd`：删除包括光标所在行以及接下来的 n-1 行；
⑧ `dG`：删除当前光标所在行以及下面的所有行；
⑨ `D`：删除当前光标所在位置到该行行尾的所有内容；

> ❗ 以上的删除命令实际上没有真正删除而是粘贴在了剪切板，将光标移动到指定位置，使用 `p` 命令，刚刚删除的内容就粘贴到此处。

> ❗ 所有命令都请注意大小写哦！

## 2.2 输入模式

在命令模式下按 `i` (insert)则进入键盘输入模式，可在文件内输入内容。

> ✅ TIP：在  Windows Terminal 下的 vim模式，是允许使用 windows 的快捷键 `Ctrl + C/V` 的。

## 2.3 编辑模式

在命令模式下输入 `:` 则进入编辑模式，可编辑文件：删除、复制、保存、保存并退出等。

① `:x!` 保存并退出vim;
① `:w` 保存文件不退出vim；
② `:wq` 保存文件并且退出vim；
④ `:w filename` 另存为 filename 文件；
③ `:q` 不保存并退出vim(若对文件改动但未保存则指令`q`失效)；
④ `:q!` 不保存并且退出vim；
① `ZZ` 直接退出vim；
⑤ `/`：按 `/` 进入搜索，在后面输入目标内容(如destination)，然后回车；
⑥ `:l1,l2d`：删除第 l1 行到第 l2 行的全部内容；
⑦ `:12`：输入数字，然后回车，光标跳到指定行(12行)

# 3. vim基本配置

WSL 的 vim 配置文件一般都是 `~/.vimrc`，若没有的话则新建一个 `.vimrc` 文件，完整位置和文件名是 `~/.vimrc`。
`.vimrc` 的注释方式是双引号 `"` 后加注释内容。

## 3.1 设置vim配置立刻生效

```bash
"保存文件配置内容后立刻生效
autocmd BufWritePost $MYVIMRC source $MYVIMRC
```

## 3.2 设置文件的编码

```
set encoding=utf-8
```

## 3.3 显示行号

```
set nu
set number
```

## 3.4 突出显示

```
"突出显示当前行
set cursorline
set cul
"突出显示当前列
set cursorcolumn
set cuc
```

## 3.5 括号匹配显示

```
set showmatch
```

## 3.6 设置缩进

```
"设置Tab长度为4空格
set tabstop=4
"设置自动缩进长度为4空格
set shiftwidth=4
"继承前一行的缩进方式，适用于多行注释
set autoindent
```

## 3.7 设置粘贴模式

```
set paste
```

> 在Vim中通过鼠标右键粘贴时会在行首多出许多缩进和空格，通过set paste可以在插入模式下粘贴内容时不会有任何格式变形、胡乱缩进等问题。

## 3.8 显示空格和tab

```
set listchars=tab:>-,trail:-
```

## 3.9 显示状态栏和光标当前位置

```
"总是显示状态栏
set laststatus=2
"显示光标当前位置
set ruler
```

# 4. vim主题配置

> 暂未更新...

# 参考链接

[Vim教程网](https://vimjc.com/vimrc-config.html)

更多相关请关注：[WSL专栏](http://mphy.gitee.io/categories/WSL/)

**❗ 法律声明**

> 本文作者：[Murphy Chen](https://www.zhihu.com/people/ai-xiao-xi-19)
> 本文链接：http://mphy.gitee.io/WSL-4（转载注明源链接）
> 版权声明：本博客作品除特别声明外，均为原创，遵循 **署名-非商业性使用-禁止演绎 4.0 未本地化版本 [CC BY-NC-ND 4.0](https://creativecommons.org/licenses/by-nc-nd/4.0/)** 协议发布