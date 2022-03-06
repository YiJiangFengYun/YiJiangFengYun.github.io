---
title: Javascript隐式转换
date: 2022-03-06 11:45:00
updated: 2022-03-06 11:45:00
categories:
- Javascript
tags:
- Javascript
---

 toString() 和 valueOf()
    1 + '1' //'11' 整型 1 被转换成字符串 '1'，变成了 '1' + '1' = '11'
    2 * '3' // 6  ：字符串 '3' 被转换成整型 3 ，变成了 2 * 3 = 6
    --------------javascript--------------------------------------
    let o = function () {
        this.toString = () => {
            return 'my is o,'
        }
        this.valueOf = () => {
            return 99
        }
    }
    let n = new o()
    console.log(n + 'abc') // '99abc'
    console.log(n * 10) // 990
    o + '1' //"function o() {\n    this.toString = () => {\n        return 'my is o,'\n    }\n    \n    this.valueOf = () => {\n        return 99\n    }\n}"
    -------------------------------------------------------------
    加法计算，如果项A不是原始类型，如果valueOf方法存在，则会调用valueOf方法得到B，如果得到的结果B不是原始类型或者valueOf方法不存在，则如果A的
    toString方法存在，则调用toString方法，最后如果这个项还不是原始类型，则报错Uncaught TypeError: Cannot convert object to primitive value。
    乘法也是一样的
    --------------javascript---------------------------------------
    let O = function () {
        this.toString = () => {
            console.log('into toString')
            return { 'string': 'ssss' }
        }
        this.valueOf = () => {
            console.log('into valueOf')
            return { 'val': 99 }
        }
    }
    let o = new O()
    console.log(O + 'xx')
    //into valueOf
    //into toString
    // VM1904:12 Uncaught TypeError: Cannot convert object to primitive value
    ---------------------------------------------------------------
