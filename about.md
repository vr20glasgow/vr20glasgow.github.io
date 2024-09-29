---
layout: page
title: Meet the team
permalink: /about/
sort: 5
---

Meet the committee! In case you need some help or advice over the weekend, one or more of these friendly faces should be around at each event, and should be
able to at least point you in the right direction.

<div class="flexgrid">
{% for member in site.data.members %}
{% include member.html name=member.name description=member.description %}
{% endfor %}
</div>
