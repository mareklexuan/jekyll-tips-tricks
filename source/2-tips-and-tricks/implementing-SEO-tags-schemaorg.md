# Implementing SEO tags - Schema.org

_Part 4 of the "Implementing SEO tags" series. To start at the beginning, see Part 1: [Implementing SEO tags - basics](https://github.com/mareklexuan/jekyll-tips-tricks/blob/main/source/2-tips-and-tricks/implementing-SEO-tags-basics.md)_

Schema.org is the most complicated of the SEO tags. It is used to display media rich search results in SERP (search engine results page = in search results on Google.com and other search engines).

It is not implemented as a simple HTML tag, but as a JSON data inside the \<script\> HTML tag.

Schema.org can be very complex as it covers with dedicated markup many content types - from articles to products, reviews, events and much, much more. In this post we will only go through the basic structure of Schema.org markup and two examples. For more specific implementation, please see the [official Schema.org documentation](https://schema.org/docs/documents.html)

The requirements/required parameters for the Schema.org markup does not always correspond with the requirements set by Google (Schema.org usually requires less information). However, as the primary use of the Schema.org markup is to improve SEO to display better results in Google, I am using those as the requirements and what I use on my website (based on the research about those requirements).

It is a bit complex and confusing, but simply - do what Google wants, as it is why we do it.

## Schema.org basic structure

The Schema.org markup structure consists of two main parts - the HTML \<script\> element with a defined property `type`:

```html
<script type="application/ld+json">
  {}
</script>
```

And the JSON data content inside the \<script\> element:

```json
{ "@context": "https://schema.org", "@type": "WebSite", "name": "Marek Le Xuan", "url": "https://mareklexuan.com" }
```

The JSON data is written as name-value pairs (aka key-value pairs). The name (key) must be a string, written within double quotes, followed by colon:

```json
{ "name": "Marek Le Xuan" }
```

Each pair is then separated by comma (no comma after the last pair):

```json
{ "name": "Marek Le Xuan", "url": "https://mareklexuan.com" }
```

Schema.org markup always starts with the `@context` and `@type` keys. The `@context` will always have a value `https://schema.org`, to signify it is a Schema.org markup, and the `@type` will be your selected content type (website, article, review etc.)

## Schema.org for website

"WebSite" is the most basic Schema.org markup. It can be used for your non-specific content pages, like homepage. It consists of 4 components:

1. `@context` - always `https://schema.org`
2. `@type` - `WebSite`
3. `name` - name of the author
4. `URL` - URL of the website

Note: Make sure you spell the word `WebSite` correctly, with capital S.

The final output will look like this:

```html
<script type="application/ld+json">
  {
    "@context": "https://schema.org",
    "@type": "WebSite",
    "name": "Marek Le Xuan",
    "url": "https://mareklexuan.com"
  }
</script>
```

## Schema.org for a blog post

Here is an example of a Schema.org for a blog post, called "BlogPosting":

```html
<script type="application/ld+json">
  {
    "@context": "https://schema.org",
    "@type": "BlogPosting",
    "headline": "{{ page.title }}",
    "image": [
      "https://mareklexuan.com/media/meta-images/blog-post-1x1.png",
      "https://mareklexuan.com/media/meta-images/blog-post-4x3.png",
      "https://mareklexuan.com/media/meta-images/blog-post-16x9.png"
    ],
    "datePublished": "{{ page.date | date_to_xmlschema }}",
    "dateModified": "{{ page.updated | date_to_xmlschema }}",
    "author": [
      {
        "@type": "Person",
        "name": "Marek Le Xuan"
      }
    ]
  }
</script>
```

Let's break it down:

- `@type` is `BlogPosting`. Pretty straightforward.
- `headline` is the title of your page. Here I am re-using the `title` variable I have already defined in the Front Matter in the [Implementing SEO tags - Basics](https://github.com/mareklexuan/jekyll-tips-tricks/blob/main/source/2-tips-and-tricks/implementing-SEO-tags-basics.md) part.
- `image` is similar to the Open Graph and Twitter images, however Google requires three different images in aspect ratios 1:1, 4:3 and 16:9, in this order. Links to these images are added using an array (multiple comma separated values enclosed by [] brackets).
- `datePublished` is the date when your post was published. I am using the page date, taken from the file name by Jekyll, and added with the Liquid tag {{ page.date}}. I have applied a filter to change the time format to the time format required by Schema.org.
- `dateModified` is the date when your post was last modified (updated). I have created a Front Matter variable `updated`, where I am storing the date of the last update of the post (this value must be updated manually). I am storing it in the format YYYY-MM-DD, mainly because I like it and because it is the same format Jekyll uses for the publishing date of the post. And again, I have applied a filter to change the time format to the time format required by Schema.org.
- `author` is the author of the post, which in this example consists of two pieces of information - `@type` (in our case "Person", but it can also be an "Organization" for companies/brands), and the `name` of the author. As you can see, the author information is stored in an array, similar to the image, but the information of the specific author is an object, enclosed in the {} brackets. Think of it as a second level of information. It is enclosed in the {} brackets so that you can add multiple authors, each with their own information enclosed in the {} brackets and separated by comma. Markup for multiple authors would then look like this:

```json
 "author": [
      {
        "@type": "Person",
        "name": "Marek Le Xuan"
      },
      {
        "@type": "Person",
        "name": "James Bond"
      },
      {
        "@type": "Person",
        "name": "Darth Vader"
      }
    ]
```
