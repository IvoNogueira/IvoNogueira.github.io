---
layout: archive
permalink: /projects/
title: "Sample Projects by Level of Complexity"
author_profile: true
header:
  image: "/images/header_main.jpg"
---


{
    "posts": [
        {% for post in site.posts %}
        {
            "title": "{{ post.title | xml_escape }}",
            "url": "{{ site.url }}{{ post.url }}",
            "date": "{{ post.date | date_to_xmlschema }}"
        }{% unless forloop.last %},{% endunless %}
        {% endfor %}
    ]
}
