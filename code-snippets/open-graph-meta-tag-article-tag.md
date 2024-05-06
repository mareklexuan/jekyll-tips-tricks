# Add Open Graph "article:tag" meta tag

Add Open Graph "article:tag" meta tag to your website.

Open Graph "article:tag" meta tag categorizes your post into one of predefined categories. Each of your posts can have multiple tags, each contained within its own meta tag.

List of allowed tags can be found in the official Meta for Developers documentation, available at [https://developers.facebook.com/docs/news-indexing/guides/metadata-tags/](https://developers.facebook.com/docs/news-indexing/guides/metadata-tags/).

## Process

I have decided to use Jekyll's tags to match them to Open Graph tags, using a YAML data file.

White developing this Liquid template, I came across several challenges:

- If two (Jekyll) tags were matched to the same (Open Graph) tag, it would list them twice.
- It was adding unexpected spaces and extra commas to the string and the split would not work correctly.

I have decided to remove duplicates by compiling all outputted Open Graph tags into a single string (first part of the code snippet) and filtering out the duplicates while splitting them into an array, now only with unique values (second part of the code snippet).

The unexpected spaces and extra commas was caused by space and line breaks around `{{ item.og-article-tag }}`, so I have moved the comma outside of the Liquid output (before the comma was added using `join` filter) and removed all line breaks and spaces.

## Code snippet

Data file in `_data` folder

```YAML
- tag: apps
  og-article-tag: Technology

- tag: books
  og-article-tag: Books & Literature

- tag: finance
  og-article-tag: Business, Finance, & Economics
```

In your template:

```Liquid
{% capture tag-string %}
    {% unless page.tags == empty %}
        {% for tag in page.tags %}
            {% for item in site.data.post-tags %}
                {% if tag == item.tag %}
                {{ item.og-article-tag }},
                {% endif %}
            {% endfor %}
        {% endfor %}
    {% endunless %}
{% endcapture %}

{% assign tag-array = tag-string | split: "," | uniq %}
{% for item in tag-array %}
<meta property="article:tag" content="{{ item }}" />
{% endfor %}
```

## Notes

- The terminology is a bit confusing, as Open Graph uses the word "tag" for what would be generally considered "category". There used to be an Open Graph meta tag specifically for category, but it seems to be deprecated as it is no longer in the documentation.
- You can also use Jekyll's category instead of tags. I don't use categories on my website, only tags, and I like to match terminology between the systems (use tags with tags). For more information about Jekyll's tags and categories, see the official documentation ([https://jekyllrb.com/docs/posts/#tags-and-categories](https://jekyllrb.com/docs/posts/#tags-and-categories)).
- If you are using a lot of tags and it would be difficult to manage the YAML data file as in the code snippet above, I would recommend reducing the number of tags, unless you have a really large site covering many topics.
- But, if you still want to keep your tags, the alternative approach would be to instead of assigning Open Graph tag to each Jekyll tag, do the opposite, assign Jekyll tags to Open Graph tags. This way you can limit the length of your YAML data file.

```YAML
- og-article-tag: Technology
  tag: ["AI","Android","Apple"]
```

- You can also add the Open Graph tags to the Front Matter of each post and list them in the `<head>` tag directly. It is much easier to control the duplicates and to list them in your `<head>` tag, but you would have to add the Open Graph tags to each post manually and manage it from each post, instead of reusing the data you already have (categories or tags) and managing it from one central place (YAML data file).

```Front Matter
---
og-tag: ["Education & Learning", "Technology"]
---
```
