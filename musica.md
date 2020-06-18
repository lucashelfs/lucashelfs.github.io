---
layout: page
title: Música
permalink: /musica/
---

<ul class="post-list">
    {%- for post in site.categories[page.title] -%}
    <li>
    {%- assign date_format = site.minima.date_format | default: "%d/%m/%y" -%}
    <span class="post-meta">{{ post.date | date: date_format }}</span>
    <h3>
        <a class="post-link" href="{{ post.url | relative_url }}">
        {{ post.title | escape }}
        </a>
    </h3>
    {%- if site.show_excerpts -%}
        {{ post.excerpt }}
    {%- endif -%}
    </li>
    {%- endfor -%}
</ul>