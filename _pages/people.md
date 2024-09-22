---
layout: page
title: people
permalink: /people/
description:
nav: true
nav_order: 1
author_profile: false
---

{% for people in site.data.people %}
<div class="person-card">
  <div class="person-photo">
    <img src="{{ site.url }}{{ site.baseurl }}/assets/img/people/{{ people.photo }}" style="max-width:100%; height:auto; object-fit:contain;">
  </div>
  <div class="person-info">
    <h3 style="max-width:100%;">
      {{ people.name }} ({{ people.name-korean }})
    </h3>
    <p style="margin-bottom: 10px">{{ people.info }}</p>
    {% if people.research-interest %}
      <p><strong>Research Interest:</strong></p>
      {% for interest in people.research-interest %}
      <p>- {{ interest }}</p>
      {% endfor %}
    {% endif %}
    {% if people.email %}
      <p style="margin-top: 10px"><strong>E-mail:</strong> {{ people.email }}</p>
    {% endif %}
    {% if people.homepage %}
      <a href="{{ people.homepage }}" class="btn btn-sm z-depth-0" role="button">Website</a>
    {% endif %}
  </div>
</div>
{% endfor %}