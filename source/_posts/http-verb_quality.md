---
title: Verb Quality.
categories:
- HTML
tags:
- HTML
---

![table http verb quality](/images/table_http_verb_quality.png)

1. A Safe operation is an operation that does not have any effect on the original value of the resource. For example, the mathematical operation "divide by 1" is a safe operation because no matter how many times you divide a number by 1, the original value will not change.
2. An Idempotent operation is an operation that gives the same result no matter how many times you perform it. For example, the mathematical operation "multiply by zero" is idempotent because no matter how many times you multiply a number by zero, the result is always same.

So, classifying methods as Safe and Idempotent makes it easier to understand which to use to develop features and predict results in a unreliable environment of Web where a client may fire a same request again
