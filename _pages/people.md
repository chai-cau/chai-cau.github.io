---
layout: page
title: people
permalink: /people/
description:
nav: true
nav_order: 1
author_profile: false
---

<link rel="stylesheet" href="{{ '/assets/css/people-custom.css' | relative_url }}">

<h4 class="category">Faculty</h4>
{% for people in site.data.people.professor %}
<div class="person-card" style="margin-left: 20px">
  <div class="person-photo">
    <img src="{{ site.url }}{{ site.baseurl }}/assets/img/people/{{ people.photo }}">
  </div>
  <div class="person-info">
    <h3 style="max-width:100%; margin-bottom: 0.2em">
      {{ people.name }}
    </h3>
    <h3 style="max-width:100%; font-size: 1.25em">
      {{ people.name-korean }}
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
    {% if people.homepage or people.cv %}
    <div style="margin-top:10px; display:flex;">
      {% if people.homepage %}
        <a href="{{ people.homepage }}" class="btn btn-sm z-depth-0" style="width: 80px;" role="button">Website</a>
      {% endif %}
      {% if people.cv %}
        <a href="{{ people.cv }}" class="btn btn-sm z-depth-0" style="width: 60px;" role="button">CV</a>
      {% endif %}
    </div>
  {% endif %}
  </div>
</div>
{% endfor %}

{% assign people_groups = 
  "Graduate Students|grad,Undergraduate Students|undergrad" | split: "," 
%}

{% for group in people_groups %}
  {% assign parts = group | split: "|" %}
  {% assign title = parts[0] %}
  {% assign key = parts[1] %}

  <h4 class="category">{{ title }}</h4>

  <div class="people-grid">
    {% for people in site.data.people[key] %}
    <div class="person-card compact vertical">
      <div class="person-photo large">
        <img src="{{ site.url }}{{ site.baseurl }}/assets/img/people/{{ people.photo }}" 
            alt="{{ people.name }}">
      </div>
      <div class="person-info">
        <h3 class="person-name">{{ people.name }}</h3>
        <div class="person-name-ko">{{ people.name-korean }}</div>
        <p class="person-meta">{{ people.info }}</p>
        {% if people.degree %}
          <p class="person-meta">{{ people.degree }}</p>
        {% endif %}
        {% if people.research-interest %}
          <ul class="person-ri">
            {% for interest in people.research-interest %}
              <li>{{ interest }}</li>
            {% endfor %}
          </ul>
        {% endif %}
        {% if people.homepage %}
          <div class="person-links">
            <a href="{{ people.homepage }}" class="btn btn-sm z-depth-0">Website</a>
          </div>
        {% endif %}
      </div>
    </div>
    {% endfor %}
  </div>

{% endfor %}

<h4 class="category">Alumni</h4>

<div class="alumni-list">
  {% for people in site.data.people.alumni %}
    <div class="alumni-row">
      <span class="alumni-name">{{ people.name }}</span>
      <span class="alumni-name-ko">{{ people.name-korean }}</span>
      <span class="alumni-meta">{{ people.info }}</span>
    </div>
  {% endfor %}
</div>