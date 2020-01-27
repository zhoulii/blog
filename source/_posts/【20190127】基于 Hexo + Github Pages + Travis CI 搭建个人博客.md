---
title: 基于 Hexo + Github Pages + Travis CI 搭建个人博客
date: 2020-01-27 22:00:00
updated: 2020-01-27 23:52:00
tags:
---

![](https://gitee.com/totorooo/assets/raw/master/image/hexo_github_travis_cover.png)

<!-- more -->

## 01.准备工作

- 在 Github 上创建一个公开仓库，名称随意起，假设此处为 blog；
- 为 blog 仓库创建一个分支，分支名必须为 gh-pages；
- 配置 blog 仓库的 Github Pages，分支选择 gh-pages； 
- 个人电脑上需要安装好 git 与 nodejs;

## 02.安装 hexo 客户端

```shell
# 安装 hexo 客户端
npm install hexo-cli -g
```

## 03.初始化博客

```shell
# 初始化博客，会生成一个 blog1 文件夹
hexo init blog1
```

## 04.初始化仓库

- 将 Github 上的 blog 仓库拉取到本地；
- 将 blog1 文件夹内的内容复制到 blog 本地仓库中；
- 将 blog 本地仓库的变化提交到 Github 上;

## 05.生成私人令牌

通过[链接](https://github.com/settings/tokens)进入 Github 的 tokens 页面，点击页面右上方的 Generate new token 按钮创建一个新的 token，记下这个 token，后面会使用到。

![](https://gitee.com/totorooo/assets/raw/master/image/github_generate_new_token.png)

## 06.配置 Travis CI

使用 github 账号登录 travis-ci.org，然后点击加号去添加仓库。

![](https://gitee.com/totorooo/assets/raw/master/image/travis_ci_config_1.png)

勾选 blog 仓库，若 blog 仓库不存在，则先点击 Sync account 按钮，然后刷新页面，blog 仓库就会出来了。

![](https://gitee.com/totorooo/assets/raw/master/image/travis_ci_config_2.png)

配置私人令牌，NAME 的值需要与 .travis.yml 中 github-token 的值相同。

![](https://gitee.com/totorooo/assets/raw/master/image/travis_ci_config_3.png)

## 07.编写 .travis.yml

在 blog 本地仓库的根目录下创建一个名为 .travis.yml 的文件，内容如下所示。

```yaml
sudo: false
language: node_js
node_js:
  - 10 # use nodejs v10 LTS
cache: npm
branches:
  only:
    - master # build master branch only
script:
  - hexo generate # generate static files
deploy:
  provider: pages
  skip-cleanup: true
  github-token: $GH_TOKEN
  keep-history: true
  on:
    branch: master
  local-dir: public
```

## 08.配置博客路径

打开 blog 本地仓库根目录下的 _config.yml 文件，修改 url 与 root 项，具体示例如下。

```yaml
url: https://zhoulii.github.io/blog
root: /blog/
```

## 09.查看构建过程

将 blog 本地仓库的变化推送到 Github，打开 travis-ci.org，查看 build 过程。

![](https://gitee.com/totorooo/assets/raw/master/image/travis_ci_build.png)

## 10.访问博客站点

访问博客站点，验证 Travis CI 是否成功发布博客。

![](https://gitee.com/totorooo/assets/raw/master/image/blog_publish_success.png)

