---
layout: post
title: Typescript -- Combining two object.
---

```typescript
var obj1 = { a: "1" };
let obj2 = { b: 2 };
let obj = { ...obj1, ...obj2 };

console.log(`Object1: ${JSON.stringify(obj1)}`); // output: Object1: {"a":"1"}
console.log(`Object2: ${JSON.stringify(obj2)}`); // output: Object2: {"b":2}
console.log(`Object: ${JSON.stringify(obj)}`); // output: Object: {"a":"1","b":2}
```