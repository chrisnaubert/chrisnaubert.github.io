---
layout: page
title: codes
permalink: /codes/
description: A growing collection of your cool codes.
nav: true
display_categories: [work, fun]
horizontal: false
---
<div class="codes">
  {% if site.enable_project_categories and page.display_categories %}
  <!-- Display categorized codes -->
    {% for category in page.display_categories %}
      <h2 class="category">{{category}}</h2>
      {% assign categorized_codes = site.codes | where: "category", category %}
      {% assign sorted_codes = categorized_codes | sort: "importance" %}
      <!-- Generate cards for each project -->
      {% if page.horizontal %}
        <div class="container">
          <div class="row row-cols-2">
          {% for project in sorted_codes %}
            {% include codes_horizontal.html %}
          {% endfor %}
          </div>
        </div>
      {% else %}
        <div class="grid">
          {% for project in sorted_codes %}
            {% include codes.html %}
          {% endfor %}
        </div>
      {% endif %}
    {% endfor %}

  {% else %}
  <!-- Display codes without categories -->
    {% assign sorted_codes = site.codes | sort: "importance" %}
    <!-- Generate cards for each project -->
    {% if page.horizontal %}
      <div class="container">
        <div class="row row-cols-2">
        {% for project in sorted_codes %}
          {% include codes_horizontal.html %}
        {% endfor %}
        </div>
      </div>
    {% else %}
      <div class="grid">
        {% for project in sorted_codes %}
          {% include codes.html %}
        {% endfor %}
      </div>
    {% endif %}

  {% endif %}

</div>
