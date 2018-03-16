---
layout: page
title: About
description: Magic Everywhere
keywords: Chill Magic
comments: true
menu: 关于
permalink: /about/
---

Chill Magic

![](/images/ice.png)

## 联系

{% for website in site.data.social %}
* {{ website.sitename }}：[@{{ website.name }}]({{ website.url }})
{% endfor %}
