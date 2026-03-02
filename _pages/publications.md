---
layout: archive
title: "Publications"
permalink: /publications/
author_profile: true
---

{% assign sorted_pubs = site.publications | sort: 'year' | reverse %}

<style>
.publication-entry {
  text-align: justify;
  line-height: 1.75;
  margin-bottom: 1.8em;   /* 每篇文章之间间距增大 */
  font-size: 1.02rem;
}

.publication-entry a {
  text-decoration: none;
  color: inherit;
  transition: color 0.2s ease;
}

.publication-entry a:hover {
  color: #555;
}

.section-title {
  font-weight: 700;
  font-size: 1.25rem;      /* 字体变大 */
  margin-top: 2.2em;       /* 段前间距加大 */
  margin-bottom: 1.2em;    /* 段后间距加大 */
  border-bottom: 1px solid #ddd;  /* 可选：增加分隔感 */
  padding-bottom: 0.3em;
}
</style>

<div class="publications-list">

  <!-- ================= First & Corresponding ================= -->
  <div class="section-title">First & Corresponding:</div>

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

      <div class="publication-entry">
        {{ authors_list }},
        {% if pub.doi %}
          <strong>
            <a href="https://doi.org/{{ pub.doi }}">
              {{ pub.title }}
            </a>
          </strong>
        {% else %}
          <strong>{{ pub.title }}</strong>
        {% endif %},
        <em>{{ pub.venue }}</em>{% if pub.year %}, {{ pub.year }}{% elsif pub.date %}, {{ pub.date | date: "%Y" }}{% endif %}.
      </div>

    {% endif %}
  {% endfor %}


  <!-- ================= Co-author ================= -->
  <div class="section-title">Co-author:</div>

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

      <div class="publication-entry">
        {{ authors_list }},
        {% if pub.doi %}
          <strong>
            <a href="https://doi.org/{{ pub.doi }}">
              {{ pub.title }}
            </a>
          </strong>
        {% else %}
          <strong>{{ pub.title }}</strong>
        {% endif %},
        <em>{{ pub.venue }}</em>{% if pub.year %}, {{ pub.year }}{% elsif pub.date %}, {{ pub.date | date: "%Y" }}{% endif %}.
      </div>

    {% endif %}
  {% endfor %}

  <!-- Notes -->
  <div style="margin-top: 1.5em; font-size: 0.9em;">
    <strong>Notes:</strong> * indicates co-first author; # indicates corresponding author.
  </div>

</div>
