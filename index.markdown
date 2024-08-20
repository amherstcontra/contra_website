---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: default
---

{% assign first_post = site.posts.first %}
<article class="post h-entry" itemscope itemtype="http://schema.org/BlogPosting">

  <header class="post-header">
    <h1 class="post-title p-name" itemprop="name headline">{{ first_post.title | escape }}</h1>
    <p class="post-meta">Issue {{first_post.issue}}, {{first_post.semester}}</p>
  </header>

  <div class="post-content e-content" itemprop="articleBody">
    {{ first_post.content }}
    <p class="author-tag"><em>&mdash;{{ first_post.author | default: 'Anonymous' }}</em></p>
  </div>

  {%- if site.disqus.shortname -%}
    {%- include disqus_comments.html -%}
  {%- endif -%}

  <a class="u-url" href="{{ page.url | relative_url }}" hidden></a>
</article>