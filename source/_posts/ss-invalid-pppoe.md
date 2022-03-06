---
title: 宽带拨号后Shadowsocks代理无效.
date: 2022-03-06 12:00:00
updated: 2022-03-06 12:00:00
categories:
- Shadowsocks
tags:
- Shadowsocks
---

宽带拨号连接后，发现Shadowsocks代理无效，不能翻墙。原来是因为宽带适配器名字是中文的（宽带连接），解决办法是用英文重命名适配器，不要使用复杂字符，比如中文。

![Picture](/images/pppoe-name-fix.png)
[Github Issue](https://github.com/shadowsocks/shadowsocks-windows/issues/1502)
