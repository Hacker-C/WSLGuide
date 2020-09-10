---
title: 玩转WSL(7)之 nodejs 环境配置
date: 2020-09-02 20:38:55
tags: WSL
categories: WSL
---
{% cq %} 这个花了我几乎一个上午的时间！！！（小白发声，大佬莫笑）网上在 WSL 上配置 nodejs 方法大致都是去官网下载压缩包然后解压，然后解析二进制文件什么的，太麻烦了，而且不太适合 WSL。于是我最后终于找到正确且快捷的方法了，记录一下。 {% endcq %}
<!--more-->
# 0. 前言

本文 `nodejs` 的配置适用于 `WSL`，本人亲测有效（WSL Ubuntu），但是可能并不适用于其他系统。

# 1. 安装 nodejs

**通过 `Ubuntu` 的 `apt-get` 命令安装的节点版本当前已过时**。而这里通过一个 Github 项目来安装你想要的版本。
进入 https://github.com/nodesource/distributions ，看里面的 `README`，找到这里
![avatar](https://s2.ax1x.com/2020/03/03/3hOgP0.png)

执行下列的命令，选择自己需要的版本就好了

```js
# Node.js v13.x
curl -sL https://deb.nodesource.com/setup_13.x | sudo -E bash -
sudo apt-get install -y nodejs

# Node.js v12.x
curl -sL https://deb.nodesource.com/setup_12.x | sudo -E bash -
sudo apt-get install -y nodejs

# Node.js v10.x
curl -sL https://deb.nodesource.com/setup_10.x | sudo -E bash -
sudo apt-get install -y nodejs
```

# 2. 清理缓存模块

```js
sudo npm cache clean -f
```

# 3. 安装版本管理器维护 nodejs 版本

## 3.1 为什么要用版本管理器

 **节点版本管理器**（如 nvm、n） 是安装多个版本的 `node.js` 的最常见方法。建议使用版本管理器，因为版本的更改速度非常快，可以根据所使用的不同项目的需要在多个版本之间进行切换。

## 3.2 使用 n模块 管理 nodejs 版本

之所以不先推荐常用的 `nvm` 是因为我个人用 `n` 模块在 `Linux` 的体验极好，之前用了 `nvm` 但因为一些原因而报 `443 Connection refused` 错误。所以 `n` 可以作为一种长期 `nvm` 的替代方法
+ 安装 n 模块
```linux
sudo npm install -g n
```
+ 安装最新的 node 稳定版
```js
sudo n stable
```
+ 安装最新的 node 版本
```js
sudo n latest
```
+ 安装最新长期支持版
```js
sudo n lts
```
+ 安装指定的 node 版本
```js
# 后面加上版本号即可
sudo n v.12.1
```
+ 删除某一版本
```
n rm [版本号]
```

> 更多命令请参考 n 的创造者前端大佬 [tj-n-nodejs](https://github.com/tj/n)


# 4. 参考链接
+ 本文参考了 [这位CSDN博主](https://blog.csdn.net/lovefengruoqing/article/details/93364522?depth_1-utm_source=distribute.pc_relevant.none-task)
+ 微软官网 [Mcrosoft Docs WSL install nvm&Nodejs&npm](https://docs.microsoft.com/zh-cn/windows/nodejs/setup-on-wsl2#install-nvm-nodejs-and-npm)
+ n 模块创始人 [tj-n-nodejs](https://github.com/tj/n)

更多相关请关注：[WSL专栏](http://mphy.gitee.io/categories/WSL/)

**❗ 法律声明**

> 本文作者：[Murphy Chen](https://www.zhihu.com/people/ai-xiao-xi-19)
> 本文链接：http://mphy.gitee.io/WSL-7（转载注明源链接）
> 版权声明：本博客作品除特别声明外，均为原创，遵循 **署名-非商业性使用-禁止演绎 4.0 未本地化版本 [CC BY-NC-ND 4.0](https://creativecommons.org/licenses/by-nc-nd/4.0/)** 协议发布
