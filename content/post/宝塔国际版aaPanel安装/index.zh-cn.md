---
title: 宝塔国际版aaPanel安装
description: 
date: 2024-07-29
slug: aapanel-bash
image: 
categories:
    - 教程
---

> aaPanel安装脚本

------------


`Centos` 
```bash
yum install -y wget && wget -O install.sh http://www.aapanel.com/script/install_6.0_en.sh && bash install.sh aapanel
```
`Ubuntu/Deepin`
```bash
wget -O install.sh http://www.aapanel.com/script/install-ubuntu_6.0_en.sh && sudo bash install.sh aapanel
```
`Debian`
```bash
wget -O install.sh http://www.aapanel.com/script/install-ubuntu_6.0_en.sh && bash install.sh aapanel
```
`IPV6`
```bash
curl -sSO http://www.aapanel.com/script/new_install_en.sh && bash new_install_en.sh forum
```
{callout color="#d97852"}
注意：确保它是一个干净的操作系统，没有安装Apache／Nginx／php／MySQL的其他环境
{/callout}

> aaPanel管理脚本

------------


`停止`
```bash
service bt stop
```
`开始`
```bash
service bt start
```
`重启`
```bash
service bt start
```
`卸载`
```bash
service bt stop && chkconfig --del bt && rm -f /etc/init.d/bt && rm -rf /www/server/panel
```
`查看当前面板端口`
```bash
cat /www/server/panel/data/port.pl
```
`改变面板端口(Centos7)`
```bash
echo '8881' > /www/server/panel/data/port.pl && service bt restart firewall-cmd --permanent --zone=public --add-port=8881/tcp firewall-cmd --reload
```
`强制改变MySQL管理密码(例如:123456)`
```bash
cd /www/server/panel && python tools.py root 123456
```
`强制改变面板登录密码(例如:123456)`
```bash
cd /www/server/panel && python tools.py panel 123456
```
`清除登录限制`
```bash
rm -f /www/server/panel/data/*.login
```

官网:https://www.aapanel.com/