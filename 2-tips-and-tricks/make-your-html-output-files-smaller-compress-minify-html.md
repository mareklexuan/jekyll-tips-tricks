# Make your HTML output files smaller (compress/minify HTML)

Smaller file sizes means faster loading of your website, which translates into better SEO, user experience and overall better performing website.

Today I want to share with you how to minify your HTML output files, and remove any excess characters, especially comments. Comments often take up a lot of space and also contain some private information you might not want to share in your public code. (You can read more about comments in my post [How to use comments in Jekyll][1].

[1]: https://github.com/mareklexuan/jekyll-tips-tricks/blob/main/1-posts/how-to-use-comments-in-jekyll.md

There is a terminological difference between minification and compression, however they are often mixed up and interchanged, so don't get confused and search only for one.

> Minification removes whitespace and unnecessary characters (comments, optional tags etc.) to create a file with a smaller size but with the same meaning (displayed the same in the browser). Compression uses algorithm to convert it into a different format with much smaller size, like `.zip`, `.rar` or `.gzip`\* on the website. (\*_GZIP compression happens in the web server, not in Jekyll._)

## Does it still matter? Everybody has fast internet nowadays

It might be true for you and your social circle, but a big part of the world still has limited access to the internet and limited or unstable speeds. Even high-speed internet connection can be spotty, especially on mobile. So why not use every advantage you can get?

Especially when minification is free and easy to implement. On Jekyll you don't even need to add any plugins, I will show you a method made purely in Liquid.

And once you reduce the size of your HTML files, every loading speed optimization that comes after it, GZIP compression, cache, CDN, it all becomes more effective as it now works with smaller files.

## HTML minification on Jekyll using only Liquid

I am always looking for a solution to a Jekyll problem that does not involve plugins. I always prefer code snippets, for example in Liquid, because I can follow the code and learn how it work, as it is something I can read and understand, compared to a script in Ruby or JavaScript.

And there is such a solution for minification of HTML in Jekyll, using Liquid, thanks to the GitHub user [penibelst](https://github.com/penibelst). They have created a code to do it in Jekyll while you are building/rendering your website, so you can upload it to your server already minimized.

Here is the link to the repository, called [jekyll-compress-html](https://github.com/penibelst/jekyll-compress-html).

It was a very simple setup process, consisting of basically three steps:

1. From the GitHub repository, copy file `compress.html` to your `_layouts` folder.
2. In each template you want to minify (for example in `_layouts/default.html`), add Front Matter with layout variable `layout: compress`:

```
---
layout: compress
---
<html>
{{ content }}
</html>
```

3. Add configuration to your `_config.yml` file. The basic configuration to remove whitespace and comments looks like this:

```yaml
compress_html:
  clippings: all
  comments: ["<!-- ", " -->"]
```

Full documentation can be found on <https://jch.penibelst.de/>.

---

## Support me 💓

Did you find it useful? Star this repository and share it with a friend. You can also buy me a coffee. Thank you.

<br>
<a href="https://www.buymeacoffee.com/mareklexuan" target="_blank"><img src="https://cdn.buymeacoffee.com/buttons/v2/default-yellow.png" alt="Buy Me A Coffee" style="height: 53px !important;width: 192px !important;" ></a>
<br>
