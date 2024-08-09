---
title: Ubuntu常用代码
description: 
date: 2024-07-27
slug: ubuntu-bash
image: 
categories:
    - 教程
---

Ubuntu常见命令


1.  **apt命令**

- 更新源
```bash
sudo apt update
```
- 更新已安装的包
```bash
sudo apt upgrade
```
- 安装包
```bash
sudo apt install package
```
- 删除包
```bash
sudo apt remove package
```
- 删除包，包括删除配置文件等
```bash
sudo apt remove package -- purge
```

2.  **文件管理**

- 列出当前目录文件（不包括隐含文件）
```bash
ls
```
- 列出当前目录文件（包括隐含文件）
```bash
ls -a
```
- 列出当前目录下文件的详细信息
```bash
ls -l
```
- 回当前目录的上一级目录
```bash
cd ..
```
- 回上一次所在的目录
```bash
cd -
```
- 回当前用户的宿主目录
```bash
cd
```
- 显示当前工作目录
  ```bash
pwd
```
- 创建任意格式的文件
```bash
touch filename.xxx
```
- 创建一个目录
```bash
mkdir 目录名
```
- 删除一个空目录
```bash
rmdir 空目录名
```
- 删除一个文件或多个文件
```bash
rm 文件名 文件名
```
- 删除一个非空目录下的一切
```bash
rm -rf 非空目录名
```
- 将文件1移动到目录1中
```bash
mv file1 dir1
```
- 将文件1重命名为文件2
```bash
mv file1 file2
```
- 复制目录a下所有文件到目录b
```bash
cp -r a/ b
```
- 创建文件a的副本，命名为文件b
```bash
cp a b
```
- 复制文件a到目录b
```bash
cp a /b
```
- 查找路径所在范围内满足字符串匹配的文件和目录
```bash
find 路径 -name “字符串”
```

3.  **解压缩**

-  解压tar包
```bash
tar -xvf file.tar
```
-  解压tar.gz
```bash
tar -xzvf file.tar.gz
```
-  解压rar
```bash
unrar e file.rar
```
-  解压zip
```bash
unzip file.zip
```

4.  **系统管理**

- 查看内核版本
```bash
uname -a
```
- 查看磁盘信息
```bash
sudo fdisk -l
```
- 查看硬盘剩余空间
```bash
df -h
```
- 查看当前的内存使用情况
```bash
free -m
```
- 查看当前有哪些进程
```bash
ps -A
```
- 关键字查找某个进程
```bash
ps -ef | grep <关键字>
```
- 杀死进程
```bash
kill 进程号
```
- 强制杀死进程
```bash
kill -9 进程号
```
- 重启系统
```bash
reboot
```
- 关机
```bash
poweroff
```

5.  **防火墙及IPV6**

- 关闭iptables
```bash
iptables -P INPUT ACCEPT
```
```bash
iptables -P FORWARD ACCEPT
```
```bash
iptables -P OUTPUT ACCEPT
```
```bash
iptables -F
```
- 卸载iptables
```bash
apt-get purge netfilter-persistent
```
- 打开ufw防火墙
- ```bash
ufw enable
```
- 关闭ufw防火墙
```bash
ufw disable
```
- 重启ufw防火墙
```bash
ufw reload
```
- 查看已经定义的ufw规则
```bash
ufw status
```
- 允许访问20端口
```bash
ufw allow 20
```
- 拒绝访问20端口
```bash
ufw deny 20
```
- 修改DNS使纯IPV6服务器可以访问IPV4资源
```bash
mv /etc/resolv.conf /etc/resolv.conf.bak && echo -e "nameserver 2001:67c:2b0::4\nnameserver 2001:67c:2b0::6" > /etc/resolv.conf
```

7.  **其他命令**

- 安装deb格式安装包
```bash
dpkg -i filename.deb
```
- dpkg删除程序但保留配置
```bash
dpkg -r 包名
```
- dpkg删除程序且删除配置
```bash
dpkg -P 包名
```
- dpkg查看安装列表
```bash
dpkg -l
```
- dpkg搜索某个包
```bash
dpkg -S 包名
```

| 数字 | 权限 |
| :--: | :--: |
| 4 | 读R |
| 2 | 写W |
| 1 | 执行X |
| 0 | 无权 |

- 修改文件a的权限
```bash
chmod 664 a
```
- 文件a增加执行权限
```bash
chmod +x a
