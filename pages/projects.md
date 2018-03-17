---
layout: page
title: Projects
description: Magic Everywhere
keywords: Chill Magic
comments: true
menu: 项目
permalink: /projects/
---

## CVM Projects

![](/images/icon-cvm.png)

[Link](https://github.com/CVM-Projects)

[CVM](https://github.com/CVM-Projects/CVM)

[CMS-Documentation](https://github.com/CVM-Projects/CMS-Documentation)

[JitFFI](https://github.com/CVM-Projects/JitFFI)

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

## The Chill Programming Language

![](/images/icon-chill.png)

[Link](https://github.com/Chill-Language)

[ICM](https://github.com/Chill-Language/ICM)

[Chill-Documentation](https://github.com/Chill-Language/Chill-Documentation)

```
(defunc main []
	(print "Hello World!")
	(return 0))
```
