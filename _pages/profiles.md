---
layout: page
permalink: /people/
title: people
description: Group members organized by role and research area.
nav: true
nav_order: 3
---

The group is organized by academic role. Profile details are maintained in one place and rendered below.

{% assign role_order = "Principal Investigator / Faculty|Postdoctoral Researchers|PhD Students|Research Assistants / Students|Alumni" | split: "|" %}

{% for role_name in role_order %}
## {{ role_name }}

{% assign members = site.data.cv.people | where: "category", role_name %}
{% if members.size == 0 %}
No entries yet.
{% else %}
{% for person in members %}
<article style="padding: 1rem 0; border-bottom: 1px solid rgba(122,31,43,0.2); display: flex; gap: 1rem; align-items: flex-start;">
  <img src="{{ person.photo | relative_url }}" alt="{{ person.name }}" style="width: 90px; height: 90px; object-fit: cover; border-radius: 4px; border: 1px solid rgba(0,0,0,0.12);" />
  <div>
    <h3 style="margin: 0;">{{ person.name }}</h3>
    <p style="margin: 0.15rem 0 0.4rem 0;"><strong>{{ person.role }}</strong></p>
    <p style="margin: 0 0 0.45rem 0;">{{ person.research_focus }}</p>
    <p style="margin: 0 0 0.35rem 0;">{{ person.bio }}</p>
    <p style="margin: 0; font-size: 0.95rem; opacity: 0.9;">
      Email: <a href="mailto:{{ person.email }}">{{ person.email }}</a>
      {% if person.profile_url %}
      | Profile: <a href="{{ person.profile_url }}">{{ person.profile_label | default: person.profile_url }}</a>
      {% endif %}
    </p>
  </div>
</article>
{% endfor %}
{% endif %}

{% endfor %}
