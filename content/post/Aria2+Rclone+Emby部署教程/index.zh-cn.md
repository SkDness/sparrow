---
title: Aria2+Rclone+Emby部署教程
description: 
date: 2024-07-27
slug: aria2
image: 
categories:
    - 教程
---

 **安装 Aria2** 
 
```bash
wget -N git.io/aria2.sh && chmod +x aria2.sh && ./aria2.sh
```
操作菜单输入 1 开始安装。

 **安装Rclone** 
 
```bash
curl https://rclone.org/install.sh | sudo bash
```
安装完后，输入rclone config命令进行配置。
```bash
rclone config
```

 **配置自动上传脚本** 
 输入nano /root/.aria2c/aria2.conf打开 Aria2 配置文件进行修改。
 
```bash
nano /root/.aria2c/aria2.conf
```
找到“下载完成后执行的命令”，把clean.sh替换为upload.sh。
```bash
# 下载完成后执行的命令
on-download-complete=/root/.aria2c/upload.sh
```
输入nano /root/.aria2c/script.conf打开附加功能脚本配置文件进行修改。
```bash
nano /root/.aria2c/script.conf
```
有中文注释，按照自己的实际情况进行修改，第一次使用只建议修改网盘名称。
```bash
# 网盘名称(RCLONE 配置时填写的name)
drive-name=OneDrive
```
重启 Aria2 。脚本选项重启或者执行以下命令：
```bash
service aria2 restart
```
 **检查配置是否成功** 
 执行upload.sh脚本，提示success即代上传脚本能正常被调用，否则请检查与 RCLONE 有关的配置。

```bash
/root/.aria2c/upload.sh
```
- 打开实时日志并下载任意文件，出现上传成功信息即代表配置成功，否则请认真阅读教程并重新开始。
- 检查网盘是否存在相关文件，若不存在说明你搞错网盘了。

　资料来自: https://p3terx.com/archives/offline-download-of-onedrive-gdriv