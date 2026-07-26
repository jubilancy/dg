---
title: "Tags"
permalink: /tags/
layout: Post
content-type: static
---
{%- assign all_tags = "" | split: "" -%}
{%- for post in site.posts -%}
  {%- for tag in post.tags -%}
    {%- unless all_tags contains tag -%}
      {%- assign all_tags = all_tags | push: tag -%}
    {%- endunless -%}
  {%- endfor -%}
{%- endfor -%}
{%- for note in site.notes -%}
  {%- for tag in note.tags -%}
    {%- unless all_tags contains tag -%}
      {%- assign all_tags = all_tags | push: tag -%}
    {%- endunless -%}
  {%- endfor -%}
{%- endfor -%}
{%- assign sorted_tags = all_tags | sort -%}

<div class="tags-index">
  {%- for tag in sorted_tags -%}
  <a href="{{ site.baseurl }}/tags/{{ tag }}/" class="tag">{{ tag }}</a>
  {%- endfor -%}
</div>
