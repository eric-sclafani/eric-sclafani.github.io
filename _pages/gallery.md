---
layout: default
title: Gallery
description: Welcome to my gallery. I generally like to snap photos of things in nature, particularly macro photos of insects and plants. 
nav: true
nav_order: 5
---

Welcome to my gallery. I like to snap close-ups of things in nature, as well as landscapes. I typically don't edit photos, though maybe I'll learn how to do it in the future.

**Note**: some images below are being duplicated for some reason, so this page is WIP.

---

<div class="gallery">
  {% assign image_files = site.static_files | where_exp: "file", "file.path contains 'assets/img/gallery'" %}
  {% assign displayed_images = "" %}

  {% for image in image_files %}
    {% assign image_path = image.path %}
    {% assign image_name = image_path | split: '/' | last %}
    {% unless displayed_images contains image_name %}
      <div class="image">
        <img src="{{ site.baseurl }}/{{ image_path }}" alt="{{ image_name }}">
      </div>
      {% assign displayed_images = displayed_images | append: image_name | append: "," %}
    {% endunless %}
  {% endfor %}
</div>

<style>
  .gallery {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
  }

  .image {
    flex-basis: 30%;
    margin: 10px;
  }

  .image img {
    width: 100%;
    height: auto;
  }
</style>