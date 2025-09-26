---
layout: default
title: Home
---

# CTF Write-ups

Tu będę wrzucał moje krótkie write-upy i notatki z CTF.  
Najnowsze wpisy:

<ul>
{% for post in site.posts %}
  <li>
    <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
    <small>— {{ post.date | date: "%Y-%m-%d" }}</small>
    {% if post.tags %}<em> ({{ post.tags | join: ", " }})</em>{% endif %}
  </li>
{% endfor %}
</ul>
