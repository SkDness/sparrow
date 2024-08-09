---
title: Caddy反代Alist
description: 
date: 2024-07-27
slug: caddy-alist
image: 
categories:
    - 教程
---

1. Ubuntu安装

```bash
sudo apt install -y debian-keyring debian-archive-keyring apt-transport-https curl
```
```bash
curl -1sLf 'https://dl.cloudsmith.io/public/caddy/stable/gpg.key' | sudo gpg --dearmor -o /usr/share/keyrings/caddy-stable-archive-keyring.gpg
```
```bash
curl -1sLf 'https://dl.cloudsmith.io/public/caddy/stable/debian.deb.txt' | sudo tee /etc/apt/sources.list.d/caddy-stable.list
```
```bash
sudo apt update
```
```bash
sudo apt install caddy
```

2. 反代Alist

```bash
example.com {
  reverse_proxy 127.0.0.1:5244
}
```
> 将 `example.com` 替换为你自己解析后的域名。

3. 编辑文件

```bash
sudo nano /etc/caddy/Caddyfile
```
```bash
sudo systemctl reload caddy
```
```bash
sudo systemctl restart caddy
```