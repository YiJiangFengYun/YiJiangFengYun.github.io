---
layout: post
title: Typescript -- Package structure standrad.
---

Package using another package should normally take with the used package name as follow:
```typescript
//Import the package from packagepath.
import * as packageName from "packagepath";

//Use the package.
//Call a variable of the package.
console.log(packageName.variable1);

//Call a function of the package.
packageName.fun();

```
All packages should normally own its index file to do some common processes(for example,
a initialization process). Objects of a pakcage can be initialized in index file of the package. The index file is also used to export its contents from other files in the package.

```typescript
//Import the some members from other files.
import { var1 } from "./file";

//A common initialization function.
export function init() {
    //Do some initialization works.
}

//Export the all contents from the file ./file.
export * from "./file";
```