---
layout: post
title: Cocos Creator -- Cocos creator cann't use sourcemaps of modules.
---

Cocos creator builder will throw error that say "Build Failed: TypeError: Cannot read property '0' of null at C:\CocosCreator\resources\app.asar\editor\page\refine-sourcemap.js:1:1466" if the project dependency modules include sourcemaps useded and cocos creator use these sourcemaps to recreate finally sourcemaps.

Solution: Module project should build two version output, one is development version that include sourcemaps, another is production version that don't include sourcemaps. and the module package file use index file of production version. The development version is used for test normally.
