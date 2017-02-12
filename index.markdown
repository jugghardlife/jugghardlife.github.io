---
layout: default
title: Jugg's Corner
---

I'm Jugg. The origin of the name, especially when young love to play DOTA, like to play Jugg this hero. February 12, 2017, personal blog began to create, constantly updated.

<p><br /><b>My Blog:</b></p>
  <ul class="posts">
    {% for post in site.posts %}
      <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ post.url }}">{{ post.title }}</a></li>
    {% endfor %}
  </ul>

<p><b>Find me on:</b></p>

<ul>

<li><a href="https://github.com/jugghardlife">Github</a></li>

</ul>

[oss]:http://en.wikipedia.org/wiki/Open_source
