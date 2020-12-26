---
title: Get enum variable name.
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
