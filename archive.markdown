---
layout: page
title: Archive
permalink: /archive/
---

{%- assign posts_by_semester = site.posts | group_by: "semester" -%}
<div class="archive">
  {%- for semester_group in posts_by_semester -%}
  <section class="archive-semester">
    <h2 class="archive-semester-title">{{ semester_group.name }}</h2>
    {%- assign issues = semester_group.items | group_by: "issue" -%}
    {%- for issue_group in issues -%}
    <h3 class="archive-issue-title">Issue {{ issue_group.name }}</h3>
    <ul class="post-list">
      {%- for post in issue_group.items -%}
      <li>
        <h3>
          <a class="post-link" href="{{ post.url | relative_url }}">
            {{ post.title | escape }}
          </a>
        </h3>
        {%- assign article_responses = site.responses | where: "responds_to", post.slug | sort: "date" -%}
        {%- if article_responses.size > 0 -%}
        <ul class="archive-responses">
          {%- for response in article_responses -%}
          <li>
            <a href="{{ post.url | relative_url }}#response-{{ response.slug }}">{{ response.title | default: "A response" | escape }}</a>
            <span class="archive-response-meta">published with Issue {{ response.issue }}, {{ response.semester }}</span>
          </li>
          {%- endfor -%}
        </ul>
        {%- endif -%}
      </li>
      {%- endfor -%}
    </ul>
    {%- endfor -%}
  </section>
  {%- endfor -%}
</div>
