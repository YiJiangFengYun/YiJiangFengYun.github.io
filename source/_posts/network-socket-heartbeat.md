---
title: Why Do Socket Need Heartbeat.
date: 2021-08-16 19:30:00
updated: 2021-08-16 19:46:00
categories:
- Network
- Socket
tags:
- Network
- Socket
---

## Why do socket need heartbeat

Sometimes the link between the server and the client can be interrupted in a way that keeps both the server and the client unaware of the broken state of the connection

For example, If a socket client connnect to a socket server through a router, then the router network is interrupted. in this case the socket client and the socket server is unaware of the broken state of the connection. Two side sockets can send packets but the packets sended will never reach each other.
