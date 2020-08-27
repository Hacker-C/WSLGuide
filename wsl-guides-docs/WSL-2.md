---
title: 玩转WSL(2)之安装Windows Terminal
date: 2020-02-29 18:00:30
tags: WSL
categories: WSL
---
# 1. 前言
之所以要先安装 Windows Terminal，是因为在配置 oh-my-zsh 主题的时候，要进行一些操作，比如修改WSL字体、修改背景透明度、设置背景图片、设置默认打开路径等等，而 Terminal 的配置文件让这些操作都变得十分简单。

# 2. 安装 Windows Terminal
直接在 MSC Store(微软商店)平台下载安装即可，是免费的。

# 3. 配置文件
点开 Terminal，打开设置文件，如图。
![avatar](https://s1.ax1x.com/2020/08/26/dRt4EQ.png)
默认是记事本打开的，不方便编辑。可以复制里面的文件到自己的编辑器（VSCode,Submit等）中，编辑好了再复制过来。但这太麻烦，所以我推荐记事本的代替品：Notepad2。
> Notepad2下载：https://notepad2.com

下载好了Notepad2后，安装时勾选 “代替Notepad”，这样下载打开 Terminal 设置文件就是默认以 Notepad2 打开了。
设置文件里的内容不详细说明了，只讲我们需要用到的设置。其他设置内容都可以在网上查到。找到如下部分，根据自己需要和以下说明，添加自己没有的配置代码。
![terminal](https://s1.ax1x.com/2020/08/26/dRaxUg.png)

## 3.1 设置默认打开的终端
将 WSL(Ubuntu) 的 `guid` 复制，设置为开头的 `defaultProfile` 的值。
![avatar](https://s1.ax1x.com/2020/08/26/dRdTdU.png)

## 3.2 字体设置

**① 设置字体**

<font color=red>为了使终端的图标和配色以及样式等不出现乱码、显示错误，就需要设置特殊的字体来契合我们所使用的主题样式，这里推荐一种适合最契合绝大多数图标样式的字体：`Meslo Nerd Font` </font>（后续配置要用到）
> 下载：[Meslo Nerd Font](https://github.com/romkatv/powerlevel10k#meslo-nerd-font-patched-for-powerlevel10k)
Github下载慢的可以下载我上传至百度网盘的Meslo字体文件:
链接：https://pan.baidu.com/s/1twTUlF99YaD6Od5EYs3ZGA 
提取码：owyf 

下载好字体文件后，把字体文件 `.ttf` 拖入 Windows 设置中的 ‘字体设置’。然后把 Windows 字体设置中的该字体名输入至 Terminal 配置项 `fontFace` 的值，即可安装。

**② 设置字体大小**

`fontSize` 设置字体大小，值为数值。

**③ 设置字体粗细**

`fontWeight` 设置字体粗细。
```json
"fontWeight": "normal"
// 可选值："normal"、"thin"、"extra-light"、"light"、"semi-light"、"medium"、"semi-bold"、"bold"、"extra-bold"、"black"、"extra-black"
```


## 3.3 设置 Terminal 背景


**① 背景图片**
`backgroundImage` 设置背景图片，其值为所使用的背景图片的完整路径，注意 `/` 要改为双反斜杠 `\\`。
例如 `E:/xxx/yyy.jpg` => `E:\\xxx\\yyy.jpg`

**② 透明度**
`backgroundImageOpacity` 设置背景透明度，其值为 `0~1` 的小数。

## 3.4 配置初始打开路径
`startingDirectory` 设置初始打开路径，使用以下格式：
```json
"startingDirectory": "//wsl$/"
// 并用分发的名称进行替换。 例如:
"startingDirectory": "//wsl$/Ubuntu-20.04"
// 我设置的是 `~`，其设置如下
"startingDirectory": "//wsl$/Ubuntu/home/murphy"
```

## 3.5 下拉列表设置

`hidden` 项设置 Terminal 的下拉表显示
```json
// 设置为 false 表示不隐藏
"hidden": false 
```

## 3.6 设置终端的名字和图标

**① `name` 项设置终端的名称**
```json
"name": "Ubuntu"
```

**② 设置终端图标**
`icon` 项设置图标，值为图标的路径
```json
"icon": "E:\\pictures\\ubuntu.jpg"
```

## 3.7 光标设置

**① 设置光标形状**
`cursorShape` 设置光标形状
```json
"cursorShape": "bar"
// 可选值："bar" (┃)、"vintage" (▃)、"underscore" (▁)、"filledBox" (█)、"emptyBox" (▯)
```

**② 设置光标颜色**
`cursorColor` 设置光标颜色
```json
"cursorColor": "#rrggbb"
// 其值为十六进制表示的颜色值
```

**③ 设置光标高度**
`cursorHeight` 设置光标高度，仅对将 cursorShape 设置为 "vintage" 有效。
```json
"cursorShape": "vintage"
"cursorHeight"： 50
// 可选值：[25， 100]
```

## 3.8 Acrylic 毛玻璃效果设置

**① 启用Acrylic**
```json
"useAcrylic": true
```
② 不透明度
```json
"acrylicOpacity": 0.6
// 可选值：0~1 的小数
```

# 4. 参考链接
[MCS Windows Terminal](https://docs.microsoft.com/zh-cn/windows/terminal/)

更多相关请关注：[WSL专栏](http://localhost:4000/categories/WSL/)

**❗ 法律声明**

> 本文作者：[Murphy Chen](https://www.zhihu.com/people/ai-xiao-xi-19)
> 本文链接：http://mphy.gitee.io/WSL-2（转载注明源链接）
> 版权声明：本博客作品除特别声明外，均为原创，遵循 **署名-非商业性使用-禁止演绎 4.0 未本地化版本 [CC BY-NC-ND 4.0](https://creativecommons.org/licenses/by-nc-nd/4.0/)** 协议发布