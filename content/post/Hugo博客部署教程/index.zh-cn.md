---
title: Hugo博客部署教程
description: 本博客部署教程，并使用Stack主题
date: 2024-07-27
slug: hugo
image: 
categories:
    - 教程
---

## 安装Hugo

1. 更新包列表并安装Hugo：
    ```bash
    sudo apt update
    ```
    ```bash
    sudo apt install hugo
    ```
2. 验证Hugo安装：
    ```bash
    hugo version
    ```

## 创建新博客

1. 创建一个新的Hugo站点：
    ```bash
    hugo new site myblog
    ```

2. 进入新创建的博客目录：
    ```bash
    cd myblog
    ```

## 安装Stack主题

1. 添加Stack主题作为子模块：
    ```bash
    git init
    ```
    ```bash
    git submodule add https://github.com/CaiJimmy/hugo-theme-stack/ themes/hugo-theme-stack
    ```

2. 复制示例配置文件：
    ```bash
    cp themes/hugo-theme-stack/config.yaml .
    ```

3. 删除默认的配置文件：
    ```bash
    rm config.toml
    ```

## 启动本地服务器

1. 启动Hugo本地服务器以查看博客：
    ```bash
    hugo server -t hugo-theme-stack
    ```

2. 打开浏览器并访问 `http://localhost:1313` 查看博客。

## 部署到服务器

1. 生成静态文件：
    ```bash
    hugo -t hugo-theme-stack
    ```

2. 将生成的 `public` 目录下的文件上传到你的Web服务器。

这样，你就可以在Debian 12服务器上成功安装并运行Hugo博客，并使用Stack主题了。

## Caddy反代

yourdomain {
    root * /xxx/xxx/public
    file_server
}