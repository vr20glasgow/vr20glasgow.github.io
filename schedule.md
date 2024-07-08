---
layout: page
title: Schedule
permalink: /schedule/
sort: 2
---

Page about the schedule. It's all in one place now, but it doesn't have to be.

{% assign days = site.data.schedule | sort %}
{% for day in days %}

## {{day[1].overview}}

{% assign thisday = day[1].items %}
{% include timeline.html day=thisday %}
{% endfor %}
