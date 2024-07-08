---
layout: page
title: Meet the team
permalink: /about/
---

Meet the committee! These are some of their names with an AI portrait and a tiny
description.

{% for member in site.data.members %}
{% include member.html name=member.name description=member.description %}
{% endfor %}
