---
layout: page
title: supervision
permalink: /students/
description: 
nav: true
nav_order: 3
display_categories: [current, alumni]
horizontal: false
---

<!-- pages/students.md -->
<div class="projects">
{%- if site.enable_student_categories and page.display_categories %}
  <!-- Display categorized students -->
  {%- for category in page.display_categories %}
  <h2 class="category">{{ category }}</h2>
  {%- assign categorized_students = site.students | where: "category", category -%}
  {%- assign sorted_students = categorized_students | sort: "importance" %}
  <!-- Generate cards for each student -->
  {% if page.horizontal -%}
  <div class="container">
    <div class="row row-cols-2">
    {%- for student in sorted_students -%}
      {% include students_horizontal.html %}
    {%- endfor %}
    </div>
  </div>
  {%- else -%}
  <div class="grid">
    {%- for student in sorted_students -%}
      {% include students.html %}
    {%- endfor %}
  </div>
  {%- endif -%}
  {% endfor %}

{%- else -%}
<!-- Display students without categories -->
  {%- assign sorted_students = site.students | sort: "importance" -%}
  <!-- Generate cards for each student -->
  {% if page.horizontal -%}
  <div class="container">
    <div class="row row-cols-2">
    {%- for student in sorted_students -%}
      {% include students_horizontal.html %}
    {%- endfor %}
    </div>
  </div>
  {%- else -%}
  <div class="grid">
    {%- for student in sorted_students -%}
      {% include students.html %}
    {%- endfor %}
  </div>
  {%- endif -%}
{%- endif -%}
</div>
