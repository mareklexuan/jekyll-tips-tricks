# Add RSS 2.0 feed

Add basic RSS 2.0 feed.

## Process

- Create file feed.xml in your root directory.
- Use Liquid to generate the XML feed file, listing 10 newest posts.

## Code snippet

RSS feed file:

```HTML

---
layout: null
---

<?xml version="1.0" encoding="UTF-8"?>
<rss version="2.0">

<channel>
	<title>{{ site.name | xml_escape }}</title>
	<link>{{ site.url }}</link>
	<description>{{ site.description | xml_escape }}</description>
	<lastBuildDate>{% for post in site.posts limit:1 %}{{ post.date | date_to_rfc822 }}{% endfor %}</lastBuildDate>
	{% for post in site.posts limit:10 %}
		<item>
			<title>{{ post.title | xml_escape }}</title>
			<link>{{ site.url }}{{ post.url }}</link>
			<guid isPermaLink="true">{{ site.url }}{{ post.url }}</guid>
			<description>{{ post.description | xml_escape }}</description>
			<pubDate>{{ post.date | date_to_rfc822 }}</pubDate>
		</item>
	{% endfor %}
</channel>
</rss>

```

## Notes

- To add feed to the website, you need to link it inside the `<head>` tag.

```HTML
<link rel="alternate" type="application/rss+xml" title="RSS Feed for My Website"  href="feed.xml" />
```

- I have placed the feed to the root directory of the website, but you can place it in the subdirectory. Popular blogging services generate feeds into subdirectories like `feed`, `feeds` or `rss`.
- The use of RSS feeds is declining, mainly because websites can't monetize them. However they are still being used by many websites and readers (people and tools/services), and they can still be used by different tools and services to display your newest post. For example I use it to show the newest posts on my GitHub profile page.
