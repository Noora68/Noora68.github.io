---
layout: archive
title: "Publications"
permalink: /publications/
author_profile: true
---
{% for publication in site.publications %}
- **{{ publication.title }}**, {{ publication.authors | join: ", " }}, _{{ publication.venue }}_, {{ publication.year }}
{% endfor %}
