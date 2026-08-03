---
layout: default
title: Home
---

{% assign posts = site.posts %}
{% assign lead = posts.first %}
{% assign rest = posts | slice: 1, 4 %}
{% assign feed = posts | slice: 1, 8 %}

{% if lead %}
<section class="lead">
  <div class="lead__eyebrow">{{ lead.category | default: "Top Story" }}</div>
  <h2 class="lead__headline"><a href="{{ lead.url | relative_url }}">{{ lead.title }}</a></h2>
  {% if lead.dek %}<p class="lead__dek">{{ lead.dek }}</p>{% endif %}
  <div class="byline">By {{ lead.author | default: site.author }} · {{ lead.date | date: "%B %-d, %Y" }}</div>
</section>
{% endif %}

<div class="content-grid">
  <section class="story-list">
    {% for post in rest %}
      <article class="story">
        <span class="story__eyebrow">{{ post.category | default: "News" }}</span>
        <h3 class="story__headline"><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h3>
        {% if post.dek %}<p class="story__dek">{{ post.dek }}</p>{% endif %}
        <div class="byline">By {{ post.author | default: site.author }} · {{ post.date | date: "%B %-d, %Y" }}</div>
      </article>
    {% endfor %}
    {% unless posts.size > 0 %}
      <p>No stories published yet. Add a file to <code>_posts/</code> to see it appear here.</p>
    {% endunless %}
  </section>

  <aside class="sidebar">
    <h4 class="sidebar__title">Latest on the wire</h4>
    <ul class="wire-feed">
      {% for post in feed %}
        <li>
          <time>{{ post.date | date: "%b %-d, %H:%M" }}</time>
          <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
        </li>
      {% endfor %}
    </ul>
  </aside>
</div>
