---
title: "Taxonomies"
permalink: /taxonomies/
layout: Post
content-type: static
---
{%- assign all_tags = "" | split: "" -%}
{%- assign all_categories = "" | split: "" -%}

{%- for post in site.posts -%}
  {%- for tag in post.tags -%}
    {%- unless all_tags contains tag -%}
      {%- assign all_tags = all_tags | push: tag -%}
    {%- endunless -%}
  {%- endfor -%}
  {%- for category in post.categories -%}
    {%- unless all_categories contains category -%}
      {%- assign all_categories = all_categories | push: category -%}
    {%- endunless -%}
  {%- endfor -%}
{%- endfor -%}

{%- for note in site.notes -%}
  {%- for tag in note.tags -%}
    {%- unless all_tags contains tag -%}
      {%- assign all_tags = all_tags | push: tag -%}
    {%- endunless -%}
  {%- endfor -%}
  {%- for category in note.categories -%}
    {%- unless all_categories contains category -%}
      {%- assign all_categories = all_categories | push: category -%}
    {%- endunless -%}
  {%- endfor -%}
{%- endfor -%}

{%- assign lists_files = site.pages | where_exp: "p", "p.url contains '/lists/'" -%}
{%- for list in lists_files -%}
  {%- for tag in list.tags -%}
    {%- unless all_tags contains tag -%}
      {%- assign all_tags = all_tags | push: tag -%}
    {%- endunless -%}
  {%- endfor -%}
  {%- for category in list.categories -%}
    {%- unless all_categories contains category -%}
      {%- assign all_categories = all_categories | push: category -%}
    {%- endunless -%}
  {%- endfor -%}
{%- endfor -%}

{%- assign sorted_tags = all_tags | sort -%}
{%- assign sorted_categories = all_categories | sort -%}

<h2>Categories</h2>
<div class="tags-index">
  {%- for category in sorted_categories -%}
  <a href="{{ site.baseurl }}/categories/{{ category }}/" class="tag">{{ category }}</a>
  {%- endfor -%}
</div>

<h2>Tags</h2>
<div class="tags-index">
  {%- for tag in sorted_tags -%}
  <a href="{{ site.baseurl }}/tags/{{ tag }}/" class="tag">{{ tag }}</a>
  {%- endfor -%}
</div>
