---
title: Zip operation for files
date: 2020-12-27 20:11:00
updated: 2020-12-27 20:11:00
categories:
- Node.js
tags:
- Node.js
- Javascript
---

## Install

```sh
npm install jszip
```

## Usage

### Zip json files in a directory

```js
const path = require("path");
const fs = require("fs");
const fsExtra = require("fs-extra");
const glob = require("glob");
const jszip = require("jszip");

function globPromise(pattern) {
    return new Promise((resolve, reject) => {
        glob(pattern, (err, files) => {
            if (err) return reject(err);
            resolve(files);
        });
    });
}

function zipJsonFiles(dirSrc, pathSrcGlob, pathDst) {
    return Promise.resolve()
    .then(() => {
        return globPromise(path.join(dirSrc, pathSrcGlob));
    })
    .then((files) => {
        return new Promise((resolve, reject) => {
            var zip = new jszip();
            const len = files.length;
            for (let i = 0; i < len; ++i) {
                zip.file(path.relative(dirSrc, files[i]), fsExtra.readFile(files[i]));
            }

            zip.generateAsync({ 
                type: "base64",
                compression: "DEFLATE",
            })
            .then((res) => {
                fs.writeFileSync(pathDst, res);
            })
            .then(() => {
                resolve();
            })
            .catch((err) => {
                reject(err);
            });

        });
    });
}

function main() {
    zipJsonFiles("config", "**/*.json", "config.zip");
}

main();
```

### Unzip file to files

```js
const fsExtra = require("fs-extra");
const jszip = require("jszip");

function main() {
    /**
     * @type { string[] }
     */
    const fileNames = [];

    /**
     * @type { string[] }
     */
    const fileContents = [];
    return Promise.resolve()
    .then(() => {
        return fsExtra.readFile("./config.zip", "utf-8");
    })
    .then((value) => {
        const zip = new jszip();
        return zip.loadAsync(value, { base64: true});
    })
    .then((zip) => {
        const promises = [];
        for (let filename in zip.files) {
            fileNames.push(filename);
            promises.push(zip.files[filename].async("string"));
        }
        return Promise.all(promises);
    })
    .then((strs) => {
        strs.forEach((str) => {
            fileContents.push(str);
        });
    })
    .then(() => {
        return fsExtra.ensureDir("config_unzip");
    })
    .then(() => {
        const len = fileNames.length;
        const promises = [];
        promises.length = len;
        for (let i = 0; i < len; ++i) {
            promises[i] = fsExtra.writeFile(`config_unzip/${fileNames[i]}`, fileContents[i]);
        }
        return Promise.all(promises);
    });
}

main(); //Output a series of json files at the config_unzip folder.
```
