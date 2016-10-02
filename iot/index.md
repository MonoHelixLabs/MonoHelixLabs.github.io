---
layout: default
---

<div class="home">

  <h1 class="page-heading">Posts</h1>

  <ul class="post-list">
    {% for post in site.posts %}
    {%if post.categories contains "iot" %}
      <li>
        {% assign author = site.data.people[post.author] %}

        <span class="post-meta">{{ post.date | date: "%b %-d, %Y" }}{% if post.author %} • <span itemprop="author" itemscope itemtype="http://schema.org/Person"><span itemprop="name">{{ author.name }}</span></span>{% endif %}</span>

        <h2>
          <a class="post-link" href="{{ post.url | prepend: site.baseurl }}">{{ post.title }}</a>
        </h2>

        {{ post.excerpt }}
      </li>
      {% endif %}
    {% endfor %}
  </ul>

  <p class="rss-subscribe">subscribe <a href="{{ "/feed.xml" | prepend: site.baseurl }}">via RSS</a></p>

</div>
