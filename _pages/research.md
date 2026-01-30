---
layout: single
title: "Research"
permalink: /research/
author_profile: true
---

{% comment %}
Helper rendering pattern:
- Title in quotes
- (with: coauthors) where names are linked if url exists
- Optional status/notes line
- Optional PDF link
- Abstract dropdown
{% endcomment %}

<!--
Uncomment JMP when its finished. Also move pubs to top when I finally get one 
-->

<!-- ## Job Market Paper

{% assign jmp = site.publications | where: "pub_status", "job-market-paper" | sort: "date" | reverse %}
{% for p in jmp limit:1 %}
<p>
  &quot;{{ p.title }},&quot;

  {% if p.coauthors %}
    (with:
    {% for a in p.coauthors %}
      {% if forloop.first == false %}
        {% if forloop.last %}, and {% else %}, {% endif %}
      {% endif %}
      {% if a.url %}<a href="{{ a.url }}" target="_blank" rel="noopener">{{ a.name }}</a>{% else %}{{ a.name }}{% endif %}
    {% endfor %}
    )
  {% endif %}

  {% if p.note %} ({{ p.note }}){% endif %}.
  {% if p.paperurl %} <a href="{{ p.paperurl }}">[PDF]</a>{% endif %}
</p>

{% if p.abstract %}
<details>
  <summary>Abstract</summary>
  <p>{{ p.abstract }}</p>
</details>
{% endif %}
{% endfor %} -->

## Working Papers

{% assign wps = site.publications | where: "pub_status", "working-paper" | sort: "date" | reverse %}
{% for p in wps %}
<p>
  &quot;{{ p.title }},&quot;

  {%- if p.coauthors -%}
    {{- " (with: " -}}
    {% for a in p.coauthors -%}
        {%- unless forloop.first -%}
            {% if forloop.last %}, and {% else %}, {% endif %}
        {%- endunless -%}
        {% if a.url -%}
         <a href="{{ a.url }}" target="_blank" rel="noopener">{{ a.name }}</a>
        {%- else -%}
            {{ a.name }}
        {%- endif -%}
    {%- endfor -%}
    )
  {%- endif -%}

  {%- if p.note -%} ({{ p.note }}){%- endif -%}.
  {%- if p.paperurl -%} <a href="{{ p.paperurl }}">[PDF]</a>{%- endif -%}
</p>

{% if p.abstract %}
<details>
  <summary>Abstract</summary>
  <p>{{ p.abstract }}</p>
</details>
{% endif %}
{% endfor %}

## Works in Progress

{% assign wip = site.publications | where: "pub_status", "work-in-progress" | sort: "date" | reverse %}
{% for p in wip %}
<p>
  &quot;{{ p.title }},&quot;

  {%- if p.coauthors -%}
    {{- " (with: " -}}
    {% for a in p.coauthors -%}
        {%- unless forloop.first -%}
            {% if forloop.last %}, and {% else %}, {% endif %}
        {%- endunless -%}
        {% if a.url -%}
         <a href="{{ a.url }}" target="_blank" rel="noopener">{{ a.name }}</a>
        {%- else -%}
            {{ a.name }}
        {%- endif -%}
    {%- endfor -%}
    )
  {%- endif -%}

  <!-- {% if p.note %} ({{ p.note }}){% endif %}.
  {% if p.paperurl %} <a href="{{ p.paperurl }}">[PDF]</a>{% endif %} -->

  {%- if p.note -%} ({{ p.note }}){%- endif -%}.
  {%- if p.paperurl -%} <a href="{{ p.paperurl }}">[PDF]</a>{%- endif -%}
</p>

{% if p.abstract %}
<details>
  <summary>Abstract</summary>
  <p>{{ p.abstract }}</p>
</details>
{% endif %}
{% endfor %}

## Publications

{% assign pubs = site.publications | where: "pub_status", "publication" | sort: "year" | reverse %}
{% for p in pubs %}
<p>
  &quot;{{ p.title }},&quot;

  {%- if p.coauthors -%}
    {{- " (with: " -}}
    {% for a in p.coauthors -%}
        {%- unless forloop.first -%}
            {% if forloop.last %}, and {% else %}, {% endif %}
        {%- endunless -%}
        {% if a.url -%}
         <a href="{{ a.url }}" target="_blank" rel="noopener">{{ a.name }}</a>
        {%- else -%}
            {{ a.name }}
        {%- endif -%}
    {%- endfor -%}
    )
  {%- endif -%}

  {% assign citation = "" %}

  {% if p.venue %}
    {% assign citation = citation | append: "<em>" | append: p.venue | append: "</em>" %}
  {% endif %}

  {% if p.year %}
    {% assign citation = citation | append: ", " | append: p.year %}
  {% endif %}

  {% if p.volume %}
    {% assign citation = citation | append: ", " | append: p.volume %}
  {% endif %}

  {% if p.issue %}
    {% assign citation = citation | append: "(" | append: p.issue | append: ")" %}
  {% endif %}

  {% if p.pages %}
    {% assign citation = citation | append: ", " | append: p.pages %}
  {% endif %}

  {% if p.note %}
    {% assign citation = citation | append: " (" | append: p.note | append: ")" %}
  {% endif %}

  {{ citation }}.
  {% if p.paperurl %} <a href="{{ p.paperurl }}">[PDF]</a>{% endif %}
</p>

{% if p.abstract %}
<details>
  <summary>Abstract</summary>
  <p>{{ p.abstract }}</p>
</details>
{% endif %}
{% endfor %}

