---
layout: page
title: Blog
permalink: /blog/
---

Find all my blog posts below. Or if you would like to view blog posts by categories check out here: <a href="{{ site.baseurl }}/categories/">here</a>.

<ul class="listing">
{% for post in site.posts %}
  {% capture y %}{{post.date | date:"%Y"}}{% endcapture %}
  {% if year != y %}
    {% assign year = y %}
    <li class="listing-seperator">{{ y }}</li>
    <hr style="height:3px; border:none; color:#333; background-color:#333;" >
  {% endif %}
  <style type="text/css">
    a {text-decoration: none;}
    a:hover {text-decoration: underline; color: hotpink;}
    a:visited {color: green;}
    a:active {color: blue;}
    b {font-size: 85%;}
  </style>
  <li class="listing-item">
    <a href="{{ site.baseurl }}{{ post.url }}" title="{{ post.title }}" style="fontsize: 3px; color: black;">{{ post.title }}</a>
    <strong style="font-size:100%; font-family: 'Titillium Web', sans-serif; float:right; padding-right: .5em">{{ post.date | date:"%-d %b %Y" }}</strong>
    <br>
    <b>Category: 
    {% for category in post.categories %}
    <a href="/categories/#{{ category }}" style="fontsize: 3px; color: dodgerblue;">{{ category }}</a>
    {% endfor %}
    </b>
    <!-- <time datetime="{{ post.date | date:"%-d %B %Y" }}">{{ post.date | date:"%-d %B %Y" }}</time> -->
    <hr style="opacity: 0.4;">
  </li>
{% endfor %}
</ul>
