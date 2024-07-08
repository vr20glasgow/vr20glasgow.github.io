---
layout: page
title: Schedule
permalink: /schedule/
---

Page about the schedule. It's all in one place now, but it doesn't have to be.

{% for day in site.data.schedule %}
{% assign thisday = day[1] %}
{% include timeline.html day=thisday %}
{% endfor %}
