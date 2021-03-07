---
layout: page
permalink: "search"
title: null
css: "/css/search.css"
---

<!-- <form action="/search.html" method="get">
  <label for="search-box">Search</label>
  <input type="text" id="search-box" name="query">
  <input type="submit" value="search">
  <div class="input-group">
    <div class="form-outline">
      <input type="text" id="search-box" class="form-control" name="query" />
      <label class="form-label" for="form1">Search</label>
    </div>
    <button type="submit" class="btn btn-primary">
      <i class="fa fa-search nav-search-icon"></i>
    </button>
  </div>
</form> -->

<form class="navbar-form" role="search" action="/search.html" method="get">
  <div class="input-group add-on">
    <input class="form-control" placeholder="Search" name="query" id="search-box" type="text">
    <div class="input-group-btn">
      <button class="btn btn-default" type="submit"><i class="glyphicon glyphicon-search"></i></button>
    </div>
  </div>
</form>

<div class="input-group">
  <div class="form-outline">
    <input type="search" id="form1" class="form-control" />
    <label class="form-label" for="form1">Search</label>
  </div>
  <button type="button" class="btn btn-primary">
    <i class="fas fa-search"></i>
  </button>
</div>

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
        "date": {{ post.date | jsonify }},
        "content": {{ post.content | strip_html | strip_newlines | jsonify }},
        "url": "{{ post.url | xml_escape }}"
      }
      {% unless forloop.last %},{% endunless %}
    {% endfor %}
  };
</script>
<script src="/js/lunr.js"></script>
<script src="/js/search.js"></script>