---
layout: default
title: Events 
permalink: /events/
---

<h2> Events </h2>
<ul class="post-list"> {% for post in site.categories.events %}
   <li style="list-style-type: none;">
   <h2> <a class="post-link" href="{{ post.url | prepend: site.baseurl }}">{{ post.title | escape }}</a> </h2>
      <span class="post-meta">{{ post.date | date: "%b %-d, %Y" }}</span>
   </li>
    {% endfor %}
</ul>
<!-- add dc919's google calendar?-->
