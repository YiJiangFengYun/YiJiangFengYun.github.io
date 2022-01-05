---
title: Title.
date: 2000-01-01 00:00:00
updated: 2000-01-01 00:00:00
categories:
- Unity
tags:
- Unity
- Coroutines
---

```mermaid
graph TB

   runFuncCoroutines(("StartCoroutines"))

   getEnumerator("Get the enumerator") %% Get or create the enumerator instance of the coroutines for the behavior instance by call the function.

   ifExistNextElement{"Exist next element?"} %%If the enumerator exist a next element.

   getNextElement("Get next element")

   endCoroutines(("End"))


   runFuncCoroutines --> getEnumerator

   getEnumerator --> ifExistNextElement

   ifExistNextElement --No--> endCoroutines

   ifExistNextElement --Yes--> getNextElement




```
