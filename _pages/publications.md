---
layout: archive
title: "Publications"
permalink: /publications/
author_profile: true
---
{% assign sorted_pubs = site.publications | sort: 'year' | reverse %}

<div class="publications-list">

  <!-- First & Corresponding -->
  <div style="margin-bottom: 1.5em;">
    <div><strong>First & Corresponding:</strong></div>
    <div style="margin-left: 1em; margin-top: 0.3em;">
      {% for pub in sorted_pubs %}
        {% assign is_first_corr = false %}
        {% for author in pub.authors %}
          {% if author.name == "Dong F" and (author.role == "first" or author.role == "corresponding") %}
            {% assign is_first_corr = true %}
          {% endif %}
        {% endfor %}

        {% if is_first_corr %}
          {% assign authors_list = "" %}
          {% for author in pub.authors %}
            {% assign author_text = author.name %}
            {% if author.name == "Dong F" %}
              {% assign author_text = "<strong>" | append: author_text | append: "</strong>" %}
            {% endif %}
            {% if author.shared == true %}
              {% assign author_text = author_text | append: "*" %}
            {% endif %}
            {% if author.role == "corresponding" %}
              {% assign author_text = author_text | append: "#" %}
            {% endif %}
            {% assign authors_list = authors_list | append: author_text %}
            {% unless forloop.last %}
              {% assign authors_list = authors_list | append: ", " %}
            {% endunless %}
          {% endfor %}

          <div style="text-align: justify; margin-bottom: 0.5em;">
            {{ authors_list | markdownify }}, 
            {% if pub.url %}
              <strong><a href="{{ pub.url }}">{{ pub.title }}</a></strong>
            {% else %}
              <strong>{{ pub.title }}</strong>
            {% endif %}, <em>{{ pub.venue }}</em>, {{ pub.year }}.
          </div>
        {% endif %}
      {% endfor %}
    </div>
  </div>

  <!-- Co-author -->
  <div style="margin-bottom: 1.5em;">
    <div><strong>Co-author:</strong></div>
    <div style="margin-left: 1em; margin-top: 0.3em;">
      {% for pub in sorted_pubs %}
        {% assign is_coauthor = false %}
        {% for author in pub.authors %}
          {% if author.name == "Dong F" and (author.role != "first" and author.role != "corresponding") %}
            {% assign is_coauthor = true %}
          {% endif %}
        {% endfor %}

        {% if is_coauthor %}
          {% assign authors_list = "" %}
          {% for author in pub.authors %}
            {% assign author_text = author.name %}
            {% if author.name == "Dong F" %}
              {% assign author_text = "<strong>" | append: author_text | append: "</strong>" %}
            {% endif %}
            {% if author.shared == true %}
              {% assign author_text = author_text | append: "*" %}
            {% endif %}
            {% if author.role == "corresponding" %}
              {% assign author_text = author_text | append: "#" %}
            {% endif %}
            {% assign authors_list = authors_list | append: author_text %}
            {% unless forloop.last %}
              {% assign authors_list = authors_list | append: ", " %}
            {% endunless %}
          {% endfor %}

          <div style="text-align: justify; margin-bottom: 0.5em;">
            {{ authors_list | markdownify }}, 
            {% if pub.url %}
              <strong><a href="{{ pub.url }}">{{ pub.title }}</a></strong>
            {% else %}
              <strong>{{ pub.title }}</strong>
            {% endif %}, <em>{{ pub.venue }}</em>, {{ pub.year }}.
          </div>
        {% endif %}
      {% endfor %}
    </div>
  </div>

  <!-- 符号说明 -->
  <div style="margin-top: 1em; font-size: 0.9em;">
    <strong>Notes:</strong> * indicates co-first author; # indicates corresponding author; <strong>Dong F</strong> is bolded.
  </div>

</div>

</div>
  <!-- 符号说明 -->
  <div style="margin-top: 1em; font-size: 0.9em;">
    <strong>Notes:</strong> * indicates co-first author; # indicates corresponding author; <strong>Dong F</strong> is bolded.
  </div>

</div>
