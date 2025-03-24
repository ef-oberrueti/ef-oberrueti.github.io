---
layout: default
title: Projekte
---

{% for project in site.events %}
## {{ project.title }}
{{project.short}}

()
[![image](/assets/img/{{ project.flyer }}){:style="width: 25%; text-align: center;" }]({{ project.url }})
{: refdef}

{% endfor %}