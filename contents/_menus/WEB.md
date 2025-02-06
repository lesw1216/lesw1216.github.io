---
title: web
---

# WEB

{% for item in site.web %}
- [{{ item.title }}]({{ item.url }})
{% endfor %}