---
layout: home
permalink: /
---

Welcome to my quick introduction to Jekyll!

  <ol>
    {% for post in site.walkthrough %}
      <li>
        <a href="{{ post.url | relative_url }}">{{ post.title | escape }}</a>
      </li>
    {% endfor %}
  </ol>
