---
layout: default
---

<div class="home">

  <h1 class="page-heading">Posts</h1>

  <ul class="post-list">
    {% for post in site.posts %}
      <li>

        {% if post.thumbnail %}
          <img src="{{ post.thumbnail }}" class="post-thumbnail"/> 
        {% endif%} 
        {% assign author = site.data.people[post.author] %}

        <span class="post-meta">{{ post.date | date: "%b %-d, %Y" }}{% if post.author %} • <span itemprop="author" itemscope itemtype="http://schema.org/Person"><span itemprop="name">{{ author.name }}</span></span>{% endif %}</span>

        <h2>
          <a class="post-link" href="{{ post.url | prepend: site.baseurl }}">{{ post.title }}</a>
        </h2>
        
        <div class="post-excerpt">
        {{ post.excerpt }}
        </div>
        <br/>
        <hr class="style14">
      </li>
    {% endfor %}
  </ul>

  <p class="rss-subscribe">subscribe <a href="{{ "/feed.xml" | prepend: site.baseurl }}">via RSS</a></p>

</div>
