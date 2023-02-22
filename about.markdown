---
layout: page
title: about
permalink: /about/
---

This is Shuang's documentation of the projects/assignments made for [Tom Igoe's class in the same name](https://itp.nyu.edu/classes/light/)

The source codes for this on GitHub can be found at [the repository](https://github.com/owochel/light).

Links for individual assignments:

<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>
