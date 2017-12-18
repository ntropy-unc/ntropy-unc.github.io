---
layout: default
title: Write Ups 
permalink: /writeups/
---

<h2> Write Ups </h2>
<ul class="post-list"> {% for post in site.categories.writeup %}
   <li style="list-style-type: none;">
   <h2> <a class="post-link" href="{{ post.url | prepend: site.baseurl }}">{{ post.title | escape }}</a> </h2>
      <span class="post-meta">{{ post.date | date: "%b %-d, %Y" }}</span>
   </li>
    {% endfor %}
</ul>
