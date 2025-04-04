---
layout: default
title: Projekte
keywords: Bücher, Spielzeug, Flohmarkt, Eltern, Elternkafi, Kaffee, FerienSpass, Ferienpass, Ferien, Kinder, Schule, Oberrüti, Turnhalle für Alle, Offene Turnhalle, Sport, Spass, Vorträge, Elternvorträge
---

{% for project in site.events %}
## {{ project.title }}
{{project.short}}

[![image](/assets/img/{{ project.flyer }}){:style="width: 25%; text-align: center;" }]({{ project.url }})
{: refdef}

{% endfor %}