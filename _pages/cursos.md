---
layout: page
title: Cursos
permalink: /cursos/
description: Lista de los cursos creados para la carrera de ingeniería de sistemas. El objetivo de cada curso es brindar un material de apoyo tanto para el estudiante como el docente. Al estar almacenados en GitHub y ser de código abierto, cualquiera puede utilizarlos y mejorarlos siempre y cuando se den los respectivos créditos a los autores.
nav: true
nav_order: 3
display_categories: [2024-I, 2024-II]
horizontal: false
social: true
---

<!-- pages/cursos.md -->
<div class="cursos">
{% if site.enable_course_categories and page.display_categories %}
  <!-- Display categorized cursos -->
  {% for category in page.display_categories %}
  <a id="{{ category }}" href=".#{{ category }}">
    <h2 class="category">{{ category }}</h2>
  </a>
  {% assign categorized_cursos = site.cursos | where: "category", category %}
  {% assign sorted_cursos = categorized_cursos | sort: "importance" %}
  <!-- Generate cards for each curso -->
  {% if page.horizontal %}
  <div class="container">
    <div class="row row-cols-1 row-cols-md-2">
    {% for curso in sorted_cursos %}
      {% include cursos_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="row row-cols-1 row-cols-md-4">
    {% for curso in sorted_cursos %}
      {% include cursos.liquid %}
    {% endfor %}
  </div>
  {% endif %}
  {% endfor %}

{% else %}

<!-- Display cursos without categories -->

{% assign sorted_cursos = site.cursos | sort: "importance" %}

  <!-- Generate cards for each curso -->

{% if page.horizontal %}

  <div class="container">
    <div class="row row-cols-1 row-cols-md-2">
    {% for curso in sorted_cursos %}
      {% include cursos_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="row row-cols-1 row-cols-md-3">
    {% for curso in sorted_cursos %}
      {% include cursos.liquid %}
    {% endfor %}
  </div>
  {% endif %}
{% endif %}
</div>

<br>