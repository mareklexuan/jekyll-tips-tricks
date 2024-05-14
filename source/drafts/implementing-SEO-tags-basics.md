# Implementing SEO tags - Basics

Let's talk about technical implementations of SEO tags - meta tags, Open Graph and Schema.org. In this short series I will cover the technical aspect of SEO tags - the code implementation. I have decided to split it into four pages for each specific type of SEO tags:

1. The basics (this page)
2. [Open Graph tags](https://github.com/mareklexuan/jekyll-tips-tricks/blob/main/source/2-tips-and-tricks/implementing-SEO-tags-open-graph.md)
3. [Twitter tags](https://github.com/mareklexuan/jekyll-tips-tricks/blob/main/source/2-tips-and-tricks/implementing-SEO-tags-twitter.md)
4. [Schema.org tags](https://github.com/mareklexuan/jekyll-tips-tricks/blob/main/source/2-tips-and-tricks/implementing-SEO-tags-schemaorg.md)

I will not cover the marketing aspect of SEO, like which tag you should use, how the content of these tags should look like, how to optimize your SEO etc. SEO is a bigger discipline than adding a few tags to your website. Please do your own research to find the best approach for your project. Here are some resources to get you started:

- <https://ogp.me/>
- <https://developer.twitter.com/en/docs/twitter-for-websites/cards/overview/markup>
- <https://moz.com/learn/seo>
- <https://www.conductor.com/academy/>
- <https://www.semrush.com/blog/>

## Adding SEO tags with a plugin

The simplest way to add metadata tags to your website is by using a Jekyll plugin. The most popular Jekyll plugin to add SEO metadata tags to your website is [jekyll-seo-tag](https://github.com/jekyll/jekyll-seo-tag), developed by the Jekyll team. It will cover the basics and get you started.

## Adding SEO tags manually

Using a plugin is a quick and easy solution, but I would recommend adding everything manually. Or at least use the plugin as a start, but then either expand the tags you use, or add all tags on your own.

By adding all SEO tags manually, you will have full control over what tags you use (especially if you want to use some not very common tags) and what information is used in them. You will have one less dependency and plugin to maintain, and you will also learn a lot about meta tags and SEO in general. And while learning about each SEO tag, you will start learning about how to optimize them, so you not only have some SEO, but also a good SEO.

Knowing both sides of SEO, the technical implementation and the marketing content of each tag, is still a valuable skill today. Even more, as adding SEO tags can be done automatically with tools and plugins, like the jekyll-seo-tag plugin. So knowing a little bit more about SEO can get you a long way.

### Setup in Jekyll

The easiest way to implement SEO tags to your \<head\> section is to create a `head.html` layout in the \_includes folder. In this layout, you will save all SEO tags and other content related to the \<head\> section (linking stylesheet, javascript scripts, Google Analytics, cookie tools etc.)

Once you create this layout, you will reference it in your page and post template layouts. This way, you only need to create it once and then you can just re-use it in all your templates.

The second step is to add variables to your Front Matter in each of your pages and posts. In these variables you will store the content of the related SEO tags, such as title, description etc., which you will then reference in your templates using Liquid.

In the following sections (and next parts of this series), I will show you examples of the implementation into the HTML code. You can name your Front Matter variables anything you want, but I recommend to use the same, or as close names to the HTML tags, so you immediately know which variable is for which HTML tag.

### Title tag

In your Front Matter, create variable `title`:

```front matter
---
title: "This is page title"
---
```

In your `head.html` file, add `<title>` HTML tag, containing Liquid tag referencing the `title` variable from the Front Matter:

```html
<title>{{ page.title }}</title>
```

### Description meta tag

Description can be added the same way as the title:

```front matter
---
description: "This is page description."
---
```

However, the description HTML meta tag is different from the \<title\> tag:

```html
<meta name="description" content="{{ page.description }}" />
```

## Fallback (default) values

For each SEO variable you have in the Front Matter, create a corresponding variable in `_config.yml`, which will contain the default value. Now you can create a fallback values for your SEO tags with following process:

1. Check if there is a value for the variable in the page's Front Matter.
2. If yes, you display it. Otherwise you display the default/fallback value.

```html
{% if page.description %}
<meta name="description" content="{{ page.description }}" />
{% else %}
<meta name="description" content="{{ site.description }}" />
{% endif %}
```

## Front Matter template

It would be exhausting to manually write each variable and its contents for each page and post on your website. Instead, you can create a Front Matter template, an empty Markdown file with just the Front Matter variables predefined and keep it in your \_draft folder. Then, when creating a new page or post, you can simply duplicate it or copy-paste it to the new Markdown file. For example:

```front matter
---
layout:
title:
description:
---
```

## Instructions in notes

To make sure I fill the variables in the Front Matter correctly and consistently, I like to add a comment with instructions for each variable in my template. I can add information such as recommended length of the text, URL template for links etc.

```front matter
---
layout: # "post" or "default"
title: # max. 55 characters
description: # 70-155 characters
---
```

To learn more about comments in Jekyll, check out my page [How to use comments in Jekyll](https://github.com/mareklexuan/jekyll-tips-tricks/blob/main/source/2-tips-and-tricks/how-to-use-comments-in-jekyll.md)

## Open Graph, Twitter and Schema.org

To learn how to implement other SEO tags, check out following parts of this series:

[Part 2: Open Graph tags](https://github.com/mareklexuan/jekyll-tips-tricks/blob/main/source/2-tips-and-tricks/implementing-SEO-tags-open-graph.md)
[Part 3: Twitter tags](https://github.com/mareklexuan/jekyll-tips-tricks/blob/main/source/2-tips-and-tricks/implementing-SEO-tags-twitter.md)
[Part 4: Schema.org tags](https://github.com/mareklexuan/jekyll-tips-tricks/blob/main/source/2-tips-and-tricks/implementing-SEO-tags-schemaorg.md)
