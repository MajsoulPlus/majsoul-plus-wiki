# 雀魂 Plus

一款用于「雀魂」的可扩展专用 PC 浏览器

## 简介

雀魂 Plus 基于 Electron 开发，是一款开源的、跨平台的「雀魂」浏览器。雀魂 Plus 的浏览行为会模拟 Electron 对应版本 Chrome 浏览器行为，但同时会提供 'MajsoulPlus' UA 字段，雀魂 Plus 原则上并不提供影响浏览器与服务器通信的功能。在基本功能外，雀魂 Plus 支持安装各类插件和缓存模组来提供扩展功能以及缓存替换。

## 基本功能

- 「雀魂」专用浏览器，内置缓存机制可有效提升游戏加载速度
- 支持设置渲染比率实现超采样抗锯齿，并可保存原画分辨率截图
- 支持多开，您可以同时开启多个浏览器，每个都是独立的小号窗口
- 适配 OBS 等视频采集工具，方便录制您的精彩时刻
- 界面多语言支持（实现中），提供 English、简体中文、正體中文（台灣）、繁體中文（香港）、日本語 的支持

## 扩展资源支持

雀魂 Plus 支持`*.mspm`、`*.mspe`、`*.mspt` 格式的专用扩展资源，可提供缓存替换、游戏插件以及雀魂 Plus 工具支持。
以下是版本 v1.10.6 内置的所有扩展资源。

请注意，以下扩展并不是全部由雀魂 Plus 开发组开发的

| 名称             | 描述                                                                                                                                                                                                                                                                                |
| ---------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 千织改绿头鸭模组 | 图像来源于 [Pixabay](https://pixabay.com/zh/%E9%B8%AD-%E7%BB%BF%E5%A4%B4%E9%B8%AD-%E6%B0%B4%E7%A6%BD-%E9%B8%AD%E9%B8%9F-%E5%AE%B6%E7%A6%BD-%E6%9D%A1%E4%BE%8B%E8%8D%89%E6%A1%88-%E5%8A%A8%E7%89%A9-%E6%80%A7%E8%B4%A8-%E5%86%AC%E5%A4%A9-3848090/) ，由 Capri23auto 上传， CC0 协议 |
| 强制报番型插件   | 由 [aoarashi1988](https://github.com/aoarashi1988) 开发                                                                                                                                                                                                                             |
| 桌布制作工具     | 简单的桌布制作工具，可以快速生成桌布图像                                                                                                                                                                                                                                            |

## 下载与更新

### 下载

#### 直接获取最新版压缩文档

- [Github Release](https://github.com/MajsoulPlus/majsoul-plus-client/releases)

#### 社区维护源

| 平台                  | 维护者                                                                       | 安装命令                                                           |
| --------------------- | ---------------------------------------------------------------------------- | ------------------------------------------------------------------ |
| Homebrew Cask / macOS | [@CaptainYukinoshitaHachiman](https://github.com/CaptainYukinoshitaHachiman) | `brew cask install majsoul-plus`                                   |
| Arch User Repository  | [@BruceZhang1993](https://github.com/BruceZhang1993)                         | [参考 AUR 发布页](https://aur.archlinux.org/packages/majsoul-plus) |

### 自动更新

雀魂 Plus 浏览器内置了一个基础的自动更新功能，会在可用情况下尝试从 Github 自动获取最新发布版本并提醒更新，您可以在「设置」-「更新」中设置您要获取的版本发布类型。

雀魂 Plus 由于会尝试从 Github 服务器读取更新信息和下载资源，在中国大陆可能会因为不可抗力无法正常下载更新补丁，您可以重新下载完整浏览器进行覆盖安装。

雀魂 Plus 对于大版本更新不会尝试自动更新，您需要手动访问新版发布页面进行下载和安装操作，还请见谅。

## 快速上手

您可以阅读这篇文章[快速上手](https://github.com/MajsoulPlus/majsoul-plus-client/wiki/QuickStart)

## 扩展阅读

- [快捷键](https://github.com/MajsoulPlus/majsoul-plus-client/wiki/Shortcuts)
- [常见问题](https://github.com/MajsoulPlus/majsoul-plus-client/wiki/FAQ)

## 关于 Wiki

本 Wiki 的构建大量参考了 [poi](https://github.com/poooi/poi/wiki) 的 Wiki， poi 项目遵循 MIT 协议，请悉知
