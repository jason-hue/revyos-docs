# RevyOS
[RevyOS](https://github.com/orgs/revyos/repositories)是由RuyiSDK团队的RevyOS小队支持开发的一款针对XuanTie芯片生态的Debian优化定制发行版。

__RevyOS__ 围绕玄铁C906、C910、C920、C908等芯片提供了完整而全面的适配和优化支持，默认集成支持玄铁扩展指令集和RVV 1.0的GCC工具链，并搭载使用RVV 1.0指令集优化过的Glibc和Kernel。

目前，__RevyOS__ 在办公、网页浏览、观看视频等方面已经能满足用户的基本使用需求。

基于上述定制和优化的 __RevyOS__，在 Lichee RV，Lichee Pi 4A 等硬件平台上，能够提供优秀的性能和极佳的体验。

# 文档说明

This website is built using [Docusaurus](https://docusaurus.io/), a modern static website generator.

## 更新镜像链接
修改此文件内容 [src/components/ImageLinks.tsx](src/components/ImageLinks.tsx)

## exported functions 
`src/components/ImageLinks.tsx` 中包含所有适用的镜像最新版本和下载链接，引用最新版链接请使用 `mdx` 并使用相关函数（见： [此处用法](docs/intro.mdx)）

`src/components/LocaleImage.tsx` 中可以在 `en` 的 i18n 下使用 `file.en.ext` 的图片（如果存在），用法见[这里](i18n/en/docusaurus-plugin-content-docs/current/Installation/licheepi4a.mdx)，搜索 `<LocaleImage`

## mdx 文件
- 图片放在 `/static/img` 下，引用为 `/img/...`

## Sidebar
Sidebar 全自动索引，在每篇文章中通过 **第一个标题** 或 markdown meta
```
---
title: your title
sidebar_position: 1
---
```
确定标题和其所在的位置。

对于文件夹，可以在文件夹中放置 `_category_.json` 手动设定其标题和所在位置，见[此处](docs/adaptation/_category_.json)

## 项目列表
### 添加项目
`src/pages/projects.tsx` 下面可以添加，具体每一项意义见 `src/components/InfoCard.tsx` `InfoCardProps` 

## Links
为了解决这个问题[facebook/docusaurus issues#3372](https://github.com/facebook/docusaurus/issues/3372)，默认为所有链接后面加上了一个 `/`， 因此跳转到其他页面需要向上一级走一次

## 开发
### 本地开发

中文：
```
$ yarn start
```

英文：
```
$ yarn start --locale en
```
只可以同时开发一种语言的文档

### 构建

```
$ yarn build
```

### 翻译
#### 内容
`i18n/en/docusaurus-plugin-content-docs/current` 下与 `docs/` 目录对应的文件就是英文版

#### 页面按钮
```
$ npm run write-translations -- --locale en
```
然后在 `i18n/en` 下的 `json` 文件中翻译

