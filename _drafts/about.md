---
layout: page
title: Meet the team
permalink: /about/
sort: 5
---

Meet the committee! These are some of their names with an AI portrait and a tiny
description.
<div class="flexgrid" style="display:flex; flex-wrap: wrap; justify-content: space-between">
{% for member in site.data.members %}
{% include member.html name=member.name description=member.description %}
{% endfor %}
</div>
