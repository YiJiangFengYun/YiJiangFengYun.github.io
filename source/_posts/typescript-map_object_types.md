---
title: Types of map object
date: 2020-12-27 20:05:00
updated: 2020-12-27 20:05:00
categories:
- Typescript
tags:
- Typescript
---

```ts
const keyToVal = {
    myKey1: 'myValue1',
    myKey2: 'myValue2',
} as const; // Type keyToVal is { readonly myKey1: "myValue1"; readonly myKey2: "myValue2" }

type Keys = keyof typeof keyToVal; // "myKey1" | "myKey2"
type Values = typeof keyToVal[Keys]; //  "myValue1" | "myValue2"


const map: {[key: string]: boolean } = {};

type TypeKey = keyof typeof map; //string | number
type TpyeValue = typeof map[TypeKey]; // boolean
```
