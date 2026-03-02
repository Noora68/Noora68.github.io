---
layout: archive
title: "Publications"
permalink: /publications/
author_profile: true
---

<div style="text-align: justify; margin-bottom: 1.2em; line-height: 1.6;">

  {{ authors_list }},

  {% if pub.doi %}
    <strong>
      <a href="https://doi.org/{{ pub.doi }}" style="text-decoration: none; color: inherit;">
        {{ pub.title }}
      </a>
    </strong>
  {% else %}
    <strong>{{ pub.title }}</strong>
  {% endif %},

  <em>{{ pub.venue }}</em>{% if pub.year %}, {{ pub.year }}{% elsif pub.date %}, {{ pub.date | date: "%Y" }}{% endif %}.

</div>
