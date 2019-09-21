---
layout: archive
permalink: /posts/
title: "Posts"
modified: 2019-09-19
comments: false
author_profile: true
header:
   #overlay_image: /images/slide-code2.png
   #overlay_filter: 0.3
---

#{% include base_path %}
#{% include group-by-array collection=site.posts field="tags" %}

#{% for tag in group_names %}
#  {% assign posts = group_items[forloop.index0] %}
#  <h2 id="{{ tag | slugify }}" class="archive__subtitle">{{ tag }}</h2>
#  {% for post in posts %}
#    {% include archive-single.html %}
#  {% endfor %}
#{% endfor %}


