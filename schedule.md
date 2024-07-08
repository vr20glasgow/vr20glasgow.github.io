---
layout: page
title: Schedule
permalink: /schedule/
---

Page about the schedule. It's all in one place now, but it doesn't have to be.

{% assign days = site.data.schedule | sort: overview%}
{% for day in  site.data.schedule %}
<h3>
    {{day[1].overview}}
</h3>
{% assign thisday = day[1].items %}
{% include timeline.html day=thisday %}
{% endfor %}
