---
layout: page
title: Articles
---

<div class="article-container">
  {% for article in site.articles reversed %}
    {% unless article.draft %}
      <div>
        <h2><a href="{{ article.url }}">{{ article.title }}</a></h2>
        <div>
          <span class="publish-date">{{ article.date | date: "%B %d, %Y" }}</span>
          <span>- {{ article.author }}</span>
        </div>
        <div>
          <p>
            {{ article.excerpt }}
          </p>
          <a href="{{ article.url }}">Read More...</a>
        </div>
      </div>
      <hr>
    {% endunless %}
  {% endfor %}
</div>