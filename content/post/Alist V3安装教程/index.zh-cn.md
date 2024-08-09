---
title: Alist V3安装教程
description: 官网教程，做个备份
date: 2024-07-27
slug: alist
image: 
categories:
    - 教程
---

一键脚本仅支持Linux-x86_64/aarch64平台。

1.  **安装** 
> ●已经安装过再次执行安装会删除之前的数据，更新请使用更新命令。
 ●提示不支持https，请把双引号去掉。
```bash
curl -fsSL "https://alist.nn.ci/v3.sh" | bash -s install
```
2.  **更新** 
  ```bash
curl -fsSL "https://alist.nn.ci/v3.sh" | bash -s update
```
3.  **卸载** 
  ```bash
  curl -fsSL "https://alist.nn.ci/v3.sh" | bash -s uninstall
```

- **自定义路径**
> 默认安装在/opt/alist，要自定义安装路径，添加安装路径为第二个参数，必须是绝对路径（路径以alist结尾时直接安装到给定路径，否则会安装在给定路径alist目录下），如安装到/root：

1.  **安装**
```bash
curl -fsSL "https://alist.nn.ci/v3.sh" | bash -s install /root
```
2.  **更新** 
  ```bash
curl -fsSL "https://alist.nn.ci/v3.sh" | bash -s update /root
```
3.  **卸载** 
  ```bash
curl -fsSL "https://alist.nn.ci/v3.sh" | bash -s uninstall /root
```

  {message type="info" content="如果你忘记了密码"/}
## 随机生成一个密码
  ```bash
cd /opt/alist && ./alist admin random
```
## 手动设置一个密码,`NEW_PASSWORD`是指你需要设置的密码
```bash
cd /opt/alist && ./alist admin set NEW_PASSWORD
```
以上内容源自官方手册https://alist.nn.ci/zh/guide/install/script.html