---
layout: default
title:  "Jekyll"
tags: [jekyll]
---

# Jekyll

## How to write a Jekyll post.

* [Blogging is baked into Jekyll.](https://jekyllrb.com/docs/posts/) You write blog posts as text files and Jekyll provides everything you need to turn it into a blog.


## Page Creation

### How to embed Jekyll Tags in a page

```
{% raw %}
{% for tag in site.tags %}
  <h3>{{ tag[0] }}</h3>
  <ul>
    {% for post in tag[1] %}
      <li><a href="{{ post.url }}">{{ post.title }}</a></li>
    {% endfor %}
  </ul>
{% endfor %}
{% endraw %}
```

