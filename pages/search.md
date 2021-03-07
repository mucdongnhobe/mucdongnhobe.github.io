---
layout: default
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

<div class="post-list" id="search-results">
        <!-- {%- for post in site.tags[tag] -%}
            <div class="tag-entry">
                <a href="{{- site.url -}}{{- post.url -}}">{{- post.title -}}</a>
                <div class="entry-date">
                    <time datetime="{{- post.date | date_to_xmlschema -}}">{{- post.date | date: "%B %d, %Y" -}}</time>
                </div>
            </div>
        {%- endfor -%} -->
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