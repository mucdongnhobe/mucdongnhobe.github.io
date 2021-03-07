---
layout: page
permalink: "search"
title: "Search"
css: "/css/search.css"
---

# Search mucdongnhobe.github.io

<form action="/search.html" method="get">
  <label for="search-box">Search</label>
  <input type="text" id="search-box" name="query">
  <input type="submit" value="search">
</form>

<!-- <ul id="search-results"></ul> -->

<div id="full-tags-list">
  <div id="search-results" class="post-list">
  </div>
</div>

<script>
  window.store = {
    {% for post in site.posts %}
      "{{ post.url | slugify }}": {
        "title": "{{ post.title | xml_escape }}",
        "author": "{{ post.author | xml_escape }}",
        "category": "{{ post.category | xml_escape }}",
        "content": {{ post.content | strip_html | strip_newlines | jsonify }},
        "url": "{{ post.url | xml_escape }}"
      }
      {% unless forloop.last %},{% endunless %}
    {% endfor %}
  };
</script>
<script src="/js/lunr.js"></script>
<script src="/js/search.js"></script>