---
title: Use Cocos Creator with Socket.IO
date: 2021-09-02 10:30:00
updated: 2021-09-02 10:30:00
categories:
- Cocos Creator
tags:
- Cocos Creator
- Socket.IO
---

When use Cocos Creator with Socket.IO on Android platform, It may need to pass the path of a CA file to WebSocket constructor to create a new WebSocket instance. How to do this? We can use Class Extends and put operation of passing the path of the CA file to the constructor of sub class of WebSocket as follow:

```js
class MyWebSocket extends WebSocket {
    constructor(url, protocols) {
        console.log("This is MyWebSocket.");
        super(url, protocols, pathCAFile);
    }
}

window.WebSocket = MyWebSocket;
```

Now, Inner Socket.IO will use the class MyWebSocket to create a WebSocket instance.

This code snippet should execute before importing Socket.IO module (For example, put the code snippet to main.js created after build the project for Android platform).  
