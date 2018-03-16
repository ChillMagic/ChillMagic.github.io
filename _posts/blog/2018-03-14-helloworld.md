---
layout: post
title: Hello World!
categories: [chill, cms]
description: The first blog
keywords: Chill
---

## The Chill Language

[Documentation](https://github.com/Chill-Language/Chill-Documentation)

[ICM Interpreter](https://github.com/Chill-Language/ICM)

```
(defunc main []
	(print "Hello World!")
	(return 0))
```

## The CMS Language

[Documentation](https://github.com/CVM-Projects/CMS-Documentation)

[CVM](https://github.com/CVM-Projects/CVM)

```
.program
	.entry main

.datas
	.string #1 "Hello World!"

.func main
	.stvarb 1, cms#pointer
	loadp %1, #1, cms#pointer
	call %0, Chill#Core#print, %1
	ret
```
