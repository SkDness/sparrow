---
title: 宝塔反代Emby
description: 
date: 2024-07-29
slug: aapanel-emby
image: 
categories:
    - 教程
---

- 修改反代配置文件如下：
```
#PROXY-START/
 
client_max_body_size 5000M;
    proxy_set_header X-Real-IP $remote_addr;
    proxy_set_header X-Forwarded-For '$proxy_add_x_forwarded_for';
    proxy_set_header X-Forwarded-Proto $scheme;
    proxy_set_header Sec-WebSocket-Extensions $http_sec_websocket_extensions;
    proxy_set_header Sec-WebSocket-Key $http_sec_websocket_key;
    proxy_set_header Sec-WebSocket-Version $http_sec_websocket_version;
    proxy_cache off;
    proxy_redirect off;
    proxy_buffering off;
location / {
        proxy_pass http://ip:port;#修改为自己的IP:端口
        proxy_set_header X-Forwarded-For $remote_addr;
        proxy_ssl_verify off;
        proxy_http_version 1.1;
        proxy_set_header Host $http_host;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection "upgrade";
        proxy_read_timeout 86400;
    }
location ~* .(gif|png|jpg|css|js|woff|woff2)$
{
    proxy_pass http://ip:port;#修改为自己的IP:端口
    proxy_set_header Host $host;
    proxy_set_header X-Real-IP $remote_addr;
    proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
    proxy_set_header REMOTE-HOST $remote_addr;
    expires 12h;
}
```
- 之后开启==强制 HTTPS==，在 CDN 的 SSL/TLS 中 设置加密模式为 ==完全==。

- emby服务端配置，网络HTTPS端口，外部域名。不配置域名的话浏览器能播放，但在客户端无法播放。

- 因为客户端会解析服务器的真实IP，之后使用真实IP连接，不过CDN。