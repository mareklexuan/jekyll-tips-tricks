# Implementing SEO tags - Twitter

_Part 3 of the "Implementing SEO tags" series. To start at the beginning, see Part 1: [Implementing SEO tags - basics](https://github.com/mareklexuan/jekyll-tips-tricks/blob/main/source/2-tips-and-tricks/implementing-SEO-tags-basics.md)_

Twitter, now X, has its own SEO tags for sharing on its platform. It is very similar to the Open Graph protocol, however the HTML declaration is slightly different. They use different HTML attributes - Twitter uses "name" attribute:

```html
<meta name="twitter:title" content="This is page title" />
```

But the Open Graph protocol uses "property" attribute:

```html
<meta property="og:title" content="This is page title" />
```

Twitter calls it Twitter Card, the part of your tweet with a link - the thumbnail, title etc. For official Twitter documentation, see: <https://developer.twitter.com/en/docs/twitter-for-websites/cards/overview/abouts-cards>

## Type of the Twitter Cards

There are four types of the Twitter Cards:

- **Summary Card**: Title, description, and thumbnail.
- **Summary Card with Large Image**: Similar to the Summary Card, but with a prominently-featured image.
- **App Card**: A Card with a direct download to a mobile app.
- **Player Card**: A Card that can display video/audio/media.

You must choose which type of the Twitter Cards you want to use. The HTML tag to set card type is:

  <meta name="twitter:card" content="value" />

where the value must be one of the following: `summary`, `summary_large_image`, `app`, or `player`. No other values are permitted.

For most of the website it comes to the decision between the **Summary Card** and **Summary Card with Large Image**. I recommend choosing one and sticking to it across the whole website, to make it easier to manage. I like the **Summary Card with Large Image** as it is close to how links look when shared on Facebook (and I like consistency across all platforms).

## Twitter title

Twitter title is the title of your content as it appears in the Twitter card, similar to the Open Graph title. You can re-use your already defined title in the Front Matter:

```html
<meta name="twitter:title" content="{{ page.title }}" />
```

## Twitter description

Twitter description is the description of your content as it appears in the Twitter card, similar to the Open Graph description. You can re-use your already defined description in the Front Matter, however I recommend re-using the Open Graph description as it is shorter and Twitter also displays only limited description text:

```html
<meta name="twitter:description" content="{{ page.og-description }}" />
```

## Twitter image

Similar to the Open Graph protocol, you need to define the thumbnail image for Twitter as well. You can re-use the one from Open Graph, but Twitter uses slightly different aspect ratio for the thumbnail image and re-using the one from the Open Graph could look off on Twitter. It is best to create a separate thumbnail for Twitter, for optimal results.

You can save the path (URL) to the Twitter thumbnail in the Front Matter, similar to the Open Graph, for example:

```front matter
---
tw-image: https://mydomain.com/media/image-tw.jpg
---
```

And then referencing it in the HTML tag with Liquid:

```html
<meta name="twitter:image" content="{{ page.tw-image }}" />
```

There are ways to optimize it, so you don't have to always write full paths to the image. See the [Open Graph image section][1] in the previous post for more information.

[1]: https://github.com/mareklexuan/jekyll-tips-tricks/blob/main/source/2-tips-and-tricks/implementing-SEO-tags-open-graph.md#open-graph-image

## Twitter site

Your Twitter account.

```html
<meta name="twitter:site" content="@realperson" />
```

## Other Twitter tags

These were the standard minimum tags for sharing pages on Twitter. There are more Twitter tags available, especially for the apps and players. Full list can be found in this [reference document](https://developer.twitter.com/en/docs/twitter-for-websites/cards/overview/markup).
