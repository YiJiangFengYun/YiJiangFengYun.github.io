---
title: Game play sound in IOS brower when Iphone turn on mute.
date: 2021-02-02 11:21:00
updated: 2021-02-02 11:27:00
categories:
- Cocos Creator
tags:
- Cocos Creator
- Game Development
---

When Iphone turn on mute setting. game is mute.  
We can keep game unmute by playing first sound loaded using audio DOM element when click first button.

```ts
//Factory function
function createFirstDomAudio() {
    var enable = true;
    enable = enable && cc.sys.os === cc.sys.OS_IOS && cc.sys.isBrowser;
    var audioFirst: HTMLAudioElement;
    if (enable) {
        const url = "...";
        audioFirst = new Audio(url);
    }

    return {
        enable,
        audioFirst,
    };
}

//Instance object.
const firstDomAudio = createFirstDomAudio();

//Click event handler for first button.
function onClick() {
    if ( ! firstDomAudio.enable) return;
    firstDomAudio.audioFirst.play();
}

```
