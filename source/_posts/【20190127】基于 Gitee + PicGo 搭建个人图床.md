---
title: 基于 Gitee + PicGo 搭建个人图床
date: 2020-01-27 17:41:40
updated: 2020-01-27 19:41:00
tags:
---

![](https://gitee.com/totorooo/assets/raw/master/image/gitee_picgo_cover.png)

<!-- more -->

## 1.前提条件

- 需要在 Gitee 上创建一个公开仓库；
- 个人电脑上需要安装 nodejs；

## 2.生成 Gitee 私人令牌

在 Gitee 的设置页面可以找到私人令牌标签，按下图所示进行配置，记住生成的私人令牌。

![](https://gitee.com/totorooo/assets/raw/master/image/get_gitee_token.png)

## 3.安装 PicGo 与 Gitee 插件

下载安装 [PicGo](https://github.com/Molunerfinn/PicGo/releases)，然后打开 PicGo 的插件设置页面搜索 gitee，安装红圈中的那个插件。

![](https://gitee.com/totorooo/assets/raw/master/image/picgo_plugin_search_gitee.png)

## 4.配置 Gitee 图床

配置细节如下图所示。

![](https://gitee.com/totorooo/assets/raw/master/image/picgo_config_gitee_plugin.png)

## 5.上传图片到 Gitee 图床

上传图片后，返回的链接会自动进入剪贴板，可直接粘贴使用。

![](https://gitee.com/totorooo/assets/raw/master/image/picgo_upload_image.png)

