---
title: Subsetting font
date: 2020-12-26 12:00:00
updated: 2020-12-27 20:27:00
categories:
- Game Development
tags:
- Game Development
- Font
---

## **Minify font seamlessly**

### Install

```sh
npm install --save fontmin
```

### Usage

```js
const Fontmin = require('fontmin');

var fontmin = new Fontmin()
    .src('./*.ttf') //Source ttf files
    .use(Fontmin.glyph({ 
        text: '012345678', //Useful character set.
        hinting: false // keep ttf hint info (fpgm, prep, cvt). default = true
    }))
    .dest('output'); //output directory

fontmin.run(function (err, files) {
    if (err) {
        return console.error(err);
    }
    files.forEach(file => {
        console.info(`File: ${file.path}`);
    });
});
```
