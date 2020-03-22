---
layout: archive
permalink: /projects/
title: "Sample Projects by Level of Complexity"
author_profile: true
header:
  image: "/images/header_main.jpg"
---

{% include base_path %}

{% for post in site.posts %}
  {% include archive-single.html %}
{% endfor %}
