---
title: Get enum variable name.
date: 2020-12-26 12:00:00
updated: 2020-12-26 12:00:00
categories:
- Typescript
tags:
- Typescript
---

You can get enum variable name.

```typescript
enum EExample {
    V1,
    V2,
}

console.log(EExample[EExample.V1]) //output: "V1"
console.log(EExample[EExample.V2]) //output: "V2"
```
