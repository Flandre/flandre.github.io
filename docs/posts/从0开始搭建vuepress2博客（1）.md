---
date: 2024-03-15
title: 从0开始搭建vuepress2博客（1）
category:
  - 从0开始搭建vuepress2博客
tag:
  - blog
  - vuepress2
---
### 前言

市面上博客系统似乎特别多，本来看微微姐用 wordpress 搭建的博客，但是似乎这个是用以前世界上最好用的语言PHP写的，我个人希望定制化高一些，所以选择了 vuepress，毕竟 vue 我相对熟悉一些。

于是，从阿b找了个视频准备照猫画虎的做，但是做了一段时间后发现，实际视频中教的美化类的写法并不能适应我的实际需求，而且微博本来作为一个记录用的工具，专注于美化有点像为了碟醋报了个饺子，所以我推翻了原来的项目，从头开始。

### 开始搭建

我是基于nodejs 20.x 搭建的，默认所有人都已经拥有了 node20 的环境。

但是如果你没有 pnpm 环境，那么建议优先安装它

```bash
npm install -g pnpm
```

vuepress 的[文档](https://v2.vuepress.vuejs.org/zh/)写的非常详细，我们只需要一条命令

```bash
pnpm create vuepress blog
```

使用命令后，他会指引你创建一个 vuepress 项目，并且会帮助你创建一个 github action 的 workflow。

进入项目目录, 在根目录下添加`.gitignore`文件

```bash
.idea
.vscode
node_modules
# VuePress 默认临时文件目录
docs/.vuepress/.temp
# VuePress 默认缓存目录
docs/.vuepress/.cache
# VuePress 默认构建生成的静态文件目录
docs/.vuepress/dist
```

如果你的 git 默认的 branch 不是 main，比如我就默认用的 master，你需要将.github/workflow/deploy-docs.yml 中的 branches 改为 master

### 初始化项目

```bash
git init
git add .
git commit -m "init"
```

在 github 中创建一个 xxx.github.io 的项目，xxx 你 github 的 id，创建后, 获取到 ssh 地址

```bash
git remote add origin git@github.com:xxx/xxx.github.io.git
git push -u origin master
```

这时，你 github 的项目会自动运行 action，等待片刻后，在项目的 settings 中找到 page 选项卡，将 branch 改为 gh-pages 分支，此时，xxx.github.io 就是你的博客网站啦。
