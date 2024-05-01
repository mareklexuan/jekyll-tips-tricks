# Add sitemap

Add a simple sitemap.

## Process

- Create a `sitemap.xml` file in the root directory of your project.
- On each page and post, use Front Matter variables `published` (boolean) and `updated` (date in YYYY-MM-DD format).

## Code snippet

Front Matter

```Front Matter
---
updated: 2024-05-04
published: true
---
```

Sitemap file:

```HTML

---
layout: null
---

<?xml version="1.0" encoding="UTF-8"?>
<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">

  {% for post in site.posts %}
    {% if post.published == true %}
    <url>
      <loc>{{ site.url }}{{ post.url }}</loc>
      {% if post.updated %}
      <lastmod>{{ post.updated | date_to_xmlschema }}</lastmod>
      {% elsif post.date %}
      <lastmod>{{ post.date | date_to_xmlschema }}</lastmod>
      {% else %}
      <lastmod>{{ site.time | date_to_xmlschema }}</lastmod>
      {% endif %}
      <changefreq>monthly</changefreq>
      <priority>0.7</priority>
    </url>
    {% endif %}
  {% endfor %}

  {% for page in site.pages %}
    {% if page.published == true %}
      <url>
        <loc>{{ site.url }}{{ page.url | remove: "index.html" }}</loc>
        {% if page.updated %}
        <lastmod>{{ page.updated | date_to_xmlschema }}</lastmod>
        {% else %}
        <lastmod>{{ site.time | date_to_xmlschema }}</lastmod>
        {% endif %}
        {% if page.permalink == "/" %}
        <changefreq>weekly</changefreq>
        <priority>1.0</priority>
        {% elsif page.permalink == "/terms-of-use/" or page.permalink == "/privacy-policy/" %}
        <changefreq>yearly</changefreq>
        <priority>0.4</priority>
        {% else %}
        <changefreq>monthly</changefreq>
        <priority>0.8</priority>
        {% endif %}
      </url>
    {% endif %}
  {% endfor %}
</urlset>

```

## Notes

- Sitemap (sitemap.xml file) can be placed in subdirectory, but convention is to place it in the root directory.
