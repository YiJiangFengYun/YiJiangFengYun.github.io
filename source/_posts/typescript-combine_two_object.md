---
title: Combining two object.
date: 2020-12-26 12:00:00
updated: 2020-12-26 12:00:00
categories:
- Typescript
tags:
- Typescript
---

```typescript
var obj1 = { a: "1" };
let obj2 = { b: 2 };
let obj = { ...obj1, ...obj2 };

console.log(`Object1: ${JSON.stringify(obj1)}`); // output: Object1: {"a":"1"}
console.log(`Object2: ${JSON.stringify(obj2)}`); // output: Object2: {"b":2}
console.log(`Object: ${JSON.stringify(obj)}`); // output: Object: {"a":"1","b":2}
```
