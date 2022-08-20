---
title: Game Server Architecture
date: 2022-08-20 11:00:00
updated: 2022-08-20 11:00:00
categories:
- Game Development
tags:
- Game Development
---

![Game Server Architecture](/images/game-server-architexture(multi_maps).png)

## 为什么不把游戏数据库代理服并入到网关服呢？不并入好处有以下几点

1. 功能与名字对应，不易混淆。
2. 避免架构节点的环形依赖，更优雅。
3. 负载均衡方面更加灵活，根据带宽和计算资源情况在机器上调配部署上更灵活。
