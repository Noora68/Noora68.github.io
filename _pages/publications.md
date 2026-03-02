---
layout: archive
title: "Publications"
permalink: /publications/
author_profile: true
---
{% assign sorted_pubs = site.publications | sort: 'year' | reverse %}

<div class="publications-list">
{% for pub in sorted_pubs %}

  {% assign first_corr_list = "" %}
  {% assign coauthor_list = "" %}
  
  {% for author in pub.authors %}
    {% assign author_text = author.name %}
    
    {% if author.name == "Dong F" %}
      {% assign author_text = "<strong>" | append: author_text | append: "</strong>" %}
    {% endif %}
    
    {% if author.role == "first" or author.role == "corresponding" %}
      {% if author.shared == true %}
        {% assign author_text = author_text | append: "*" %}
      {% endif %}
      {% if author.role == "corresponding" %}
        {% assign author_text = author_text | append: "#" %}
      {% endif %}
      {% assign first_corr_list = first_corr_list | append: author_text %}
    {% else %}
      {% assign coauthor_list = coauthor_list | append: author_text %}
    {% endif %}
    
    {% unless forloop.last %}
      {% if author.role == "first" or author.role == "corresponding" %}
        {% assign first_corr_list = first_corr_list | append: ", " %}
      {% else %}
        {% assign coauthor_list = coauthor_list | append: ", " %}
      {% endif %}
    {% endunless %}
  {% endfor %}

  <!-- First & Corresponding -->
  {% if first_corr_list != "" %}
  <div style="margin-bottom: 0.2em;"><strong>First & Corresponding:</strong></div>
  <div style="margin-left: 1em; margin-bottom: 0.5em;">
    {{ first_corr_list | markdownify }}, 
    {% if pub.url %}
      <strong><a href="{{ pub.url }}" target="_blank">{{ pub.title }}</a></strong>
    {% else %}
      <strong>{{ pub.title }}</strong>
    {% endif %}, <em>{{ pub.venue }}</em>, {{ pub.year }}
  </div>
  {% endif %}

  <!-- Co-author -->
  {% if coauthor_list != "" %}
  <div style="margin-bottom: 0.2em;"><strong>Co-author:</strong></div>
  <div style="margin-left: 1em; margin-bottom: 1em;">
    {{ coauthor_list | markdownify }}, 
    {% if pub.url %}
      <strong><a href="{{ pub.url }}" target="_blank">{{ pub.title }}</a></strong>
    {% else %}
      <strong>{{ pub.title }}</strong>
    {% endif %}, <em>{{ pub.venue }}</em>, {{ pub.year }}
  </div>
  {% endif %}

{% endfor %}

<!-- 符号说明 -->
<div style="margin-top: 1em; font-size: 0.9em;">
  <strong>Notes:</strong> * indicates co-first author; # indicates corresponding author.
</div>

</div>
