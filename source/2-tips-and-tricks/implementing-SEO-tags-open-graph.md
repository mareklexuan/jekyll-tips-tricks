# Implementing SEO tags - Open Graph

_Part 2 of the "Implementing SEO tags" series. To start at the beginning, see Part 1: [Implementing SEO tags - basics](https://github.com/mareklexuan/jekyll-tips-tricks/blob/main/source/2-tips-and-tricks/implementing-SEO-tags-basics.md)_

Some meta tags are used mainly for sharing your content on social media platforms, like Facebook or Twitter (now X). The Open Graph protocol is a specific set of meta tags, primarily used by Facebook when sharing the web page on Facebook news feed or in Messenger, to create rich media previews with thumbnail, title and description.

Even though some of the Open Graph meta tags add the same information about your web page like title or description, they are not interchangeable or fallbacks for the tags mentioned in the previous post. They are separate and it is important to add them both, because Facebook, when looking for the title and description information on your web page, will ignore the other tags and will only use Open Graph tags.

There are 4 basic meta tags in Open Graph protocol - title, description, image, url - and several optional information (some generic, like type or language, and some specific, like time when an article was modified). For more information and specification of the Open Graph protocol, see <https://ogp.me/>.

## Structure of the HTML tag

Open Graph meta tags use the `property` attribute in the HTML tag, compared to the `name` attribute used in the description or Twitter tags (more about them in the next post).

## Open Graph Title

Open Graph Title will be displayed under to the thumbnail image (Open Graph image):

```html
<meta property="og:title" content="{{ page.title }}" />
```

Here we are re-using the title Front Matter variable set in the previous page, the [Implementing SEO tags - Basics](https://github.com/mareklexuan/jekyll-tips-tricks/blob/main/source/2-tips-and-tricks/implementing-SEO-tags-basics.md).

## Open Graph Description

For Open Graph description, I am using a new Front Matter variable called "og-description" as the Open Graph description has a different recommended optimal length (less than 60 characters), compared to the "standard" description (approx. 70-155 characters).

```front matter
---
og-description: "Shorter description of the page."
---
```

```html
<meta property="og:description" content="{{ page.og-description }}" />
```

## Open Graph Image

Open Graph image is a link to your thumbnail image. For optimal results, so the image fills the whole area and doesn't get cropped or warped, use the image exactly 1200 x 630 pixels (see more information in the [official documentation](https://developers.facebook.com/docs/sharing/webmasters/images/)).

You can set location of your image as variable in your Front Matter, for example like this:

```front matter
---
og-image: https://mydomain.com/media/image-og.jpg
---
```

And then reference it:

```html
<meta property="og:image" content="{{ page.og-image }}" />
```

> Note: I recommend naming your thumbnail images in format "name-og", where "name" would be replaced by the URL slug to your page, and "-og" would signify that it is a image specifically for the Open Graph (as Twitter uses a different aspect ration and would require a separate thumbnail image, but more about in the next post), for example "blog-og.jpg" or "my-first-post-og.jpg".

There are ways to tweak this process and optimize it so you write as little in the Front Matter variables as possible. If you host your images on your domain (or on a different, but all images on the same domain) and in the same folder, you don't have to specify it in the Front Matter variable and have it fixed in the HTML meta tag instead:

```front matter
---
og-image: image-og.jpg
---
```

```html
<meta property="og:image" content="https://mydomain.com/media/{{ page.og-image }}" />
```

If you followed my advice and you named your thumbnail images in a format consisting of a URL slug to the post for which the thumbnail is added, the "-og" to distinguish the mage for Open Graph, and using one file extension (for example .jpg), you can remove the Front Matter variable completely and only create a Liquid formula to get the path to the thumbnail image automatically from the page's URL. You can find the solution in the code snippet: [Automatic Open Graph og:image property using page URL](https://github.com/mareklexuan/jekyll-tips-tricks/blob/main/source/3-code-snippets/automatic-open-graph-ogimage-property.md)

## Open Graph URL

Open Graph URL is a link to the page. For this, you don't need a Front Matter variable, as your domain stays the same and the URL slug to the page is already available as Liquid tag, so you can use:

```html
<meta property="og:url" content="https://mydomain.com{{ page.url}}" />
```

## Other Open Graph tags

These were the standard minimum tags for sharing pages on Facebook (and some other social media platforms). Other very common tag is the type, defining the type of content (article, video, etc.):

```html
<meta property="og:type" content="article" />
```

There are more Open Graph tags available, especially for the articles or videos. Full list can be found in this [reference document](https://developers.facebook.com/docs/sharing/webmasters).

## Sharing Debugger

Important step in setting up Open Graph for Facebook sharing is its validation. Every time you create a new page and add Open Graph tags (or update them), you need to "load" it to Facebook by scraping it in the Sharing Debugger (there is a button to Scrape/Scrape again). It will load all values from your Open Graph meta tags and store them at Facebook, so they can be displayed when somebody is sharing your page.

If you skip this step, it will only load the values once the page is shared, so the first time somebody shares your page, it will not load all the information and will not be displayed correctly. Especially the thumbnail image, which will be missing.

It also works as a debugger (technically it is its primary purpose) which will show you what values for each Open Graph tag is used (what Facebook sees). It also warns you if some of the important tags are missing, so you can fix any issue as soon as possible.

The Sharing Debugger is available at <https://developers.facebook.com/tools/debug/>.
