---
layout: archive
permalink: /projects/
title: "Sample Projects by Level of Complexity"
author_profile: true
header:
  image: "/images/header_main.jpg"
---

<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
      {{ post.excerpt }}
    </li>
  {% endfor %}
</ul>
