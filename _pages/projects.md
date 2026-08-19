---
layout: page
title: projects
permalink: /projects/
description: Research projects and ongoing technical work.
nav: true
nav_order: 2
---

This page summarizes ongoing and completed research projects. Each project page provides additional technical detail, references, and related outputs.

{% assign sorted_projects = site.projects | sort: "importance" %}

<div class="projects">
  {% for project in sorted_projects %}
    <article style="padding: 1.25rem 0; border-bottom: 1px solid rgba(122,31,43,0.25);">
      <h3 style="margin-bottom: 0.25rem;"><a href="{{ project.url | relative_url }}">{{ project.title }}</a></h3>
      {% if project.description %}
        <p style="margin-bottom: 0.4rem;">{{ project.description }}</p>
      {% endif %}
      <p style="margin: 0; font-size: 0.95rem; opacity: 0.9;">
        {% if project.category %}
          Area: {{ project.category | capitalize }}
        {% else %}
          Area: [Research Area]
        {% endif %}
      </p>
    </article>
  {% endfor %}
</div>
