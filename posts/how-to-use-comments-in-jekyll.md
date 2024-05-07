# How to use comments in Jekyll

In general, there are two types of comments in the code - single line and multi-line comments. Single line comments end with break line and is usually used to add short description, quick info or tooltip to a specific code block, or as a heading/divider. Multi-line comments have an opening and closing tag and can contain whole paragraphs of text. They are commonly used to add description of the whole file, add settings instructions, display licence or add file index. Multi-line comments doesn’t have to be two or more lines, they can still be only on a single line, often even within a line of code.

There are no hard rules about what should be in comments and which type you should use. It all depends on your workflow and style. There are some common practices and uses, but you can be as creative with comments as you like. Do you like to have documentation in the code or in a separate document?

However, utilizing comments in the code is a valuable tool to better manage your website, especially when managed by multiple people. You don't need to educate others or build extensive external documentation, a few comments can make that for you.

It is also good for you, even if you are sole editor of your project, because over time we can forget what we have set up, what values each variable should have, or how to make changes, especially for more technical components of your Jekyll project.

Here is a collection of how to add comments in various file formats used in Jekyll and some examples on how they can help you.

## YAML

YAML only supports single line comments. Comment starts with the hashtag/pound sign `#` and ends with a line break. It can start on a new line, but it can also be after a code on the same line.

YAML comments are not rendered in your output files, they are only in the source code and ignored by Jekyll.

```yaml
# This is a comment

- name: Terms of Use
  link: /terms-of-use/ # But this is a comment too
```

The comment `#` sign must have space on the left side, otherwise it's processed as part of the YAML code. It doesn't have to have space on the right side, but it is standard practice to add it for better readability.

```yaml
- name: Terms of Use # This is a comment
  display: false #This is still a comment
  link: /terms-of-use/#but this is not
```

In general you would use comments in YAML to provide details about the variable, list permitted values, or add file description with index and some instructions.

```yaml
# -------------------------------------
# - name: {Name displayed in menu}
#   menu: {Which menu - main (header), footer}
#   display: {Show/hide item - boolean (true, false)}
#   link: {URL without domain, from root directory, e.g. /link/}
# -------------------------------------
# Ordered manually in required order in the menu
# -------------------------------------
# Index:
# - Main menu
# - Footer menu
# -------------------------------------

# Main nav menu

- name: Terms of Use # Name displayed in menu
  menu: main # Values - main, footer
  display: false # Show/hide item - boolean (true, false)
  link: /terms-of-use/ # Link from root directory
```

Obviously, if you add file instructions to your YAML data file like you see above, you don't need to add additional comments to every data record in that file. It was just to showcase different uses.

I use comments in YAML mainly to note details about variables in the `_config.yml` file, to add description of what that function does or what are allowed values. In data files I use them to add file description and instructions, similar to the one above, and add headings to break to separate sections of the data. Like in the example, separating data for main menu and footer menu.

## Front Matter

Comments in Front Matter work the same way as in YAML files.

I use comments in Front Matter to note instructions on how to set each variable. I have a template file for pages and posts in `_drafts` folder with instructions in comments.

```yaml
---
layout: post
title: "How to use comments in Jekyll" # Max n characters
tags: # Max 5 tags, in format ["jekyll","jekyll"]
updated: # Date in format YYYY-MM-DD
published: true # Show/Hide post - boolean
---
```

## HTML

HTML only has multi-line style of comments. Similarly to HTML tags, you have opening and closing tag for comments as well. HTML comments start with `<!--` and with `-->`. Notice that there is an exclamation point `!` in the start tag, but not in the end tag.

They also stay in your HTML code. They are not displayed on your website, but they stay in your code, unless you remove them when rendering your website.

Most common use is to add headings and visually separate sections of your code for easier readability. They are very useful when you have a lot of Liquid templates in your HTML code and you don't know where one section ends and another starts.

```html
<!-- Logo -->
<img> Logo </logo>
<!-- Navigation - Burger icon -->
<div> Burger icon </div>
<!-- Navigation - Menu -->
<menu> Menu </menu>
```

As HTML comments are multi-line, they can cover whole sections. They are also commonly used to temporarily deactivate parts of your HTML code, for example when you are building a new version and don’t want to delete the old code.

```html
<!-- Header - old
<img> Logo </logo>
<div> Burger icon </div>
<menu> Menu </menu>
-->

<!-- Header - new -->
<img> Logo </logo>
<div> Burger icon </div>
<menu> Menu </menu>
```

HTML comments can also be "empty", they don't have to have any content to the comments. You can use them as simple dividers.

```html
<img> Logo </logo>
<!--  -->
<div> Burger icon </div>
<!--  -->
<menu> Menu </menu>
```

## CSS

CSS also used only multi-line comments, using start and end tags. But in this case, it is `/*` and `*/`. They can also be empty as in HTML. And similar to HTML, CSS comments are not displayed in the browser, but stay in your code, unless removed.

You can use them as a divider, add headings, details about variables, add longer description, or hide parts of your code.

```css
/* Paragraph */

p {
  font-size: 16px; /* Set font size */
}

/* */

/* This is
Heading 1
*/

h1 {
  font-size: /*20px*/ 16px;
}
```

You can also use them inside the HTML `<style>` element.

```html
<style>
  p {
    font-size: 16px; /* Set font size */
  }
</style>
```

When adding comments over several lines, it is a common practice to add star symbol `*` at the beginning of each line and leave the first and last line empty, to highlight the whole comment for better readability. Or even two lines from each side, to make them extra nice.

```css
/* Instead of
comment
like this
*/

/* 
* Write
* comments
* like this
*/

/* 
*
* Or even
* like this
*
*/
```

## SCSS

In SCSS files you can use standard CSS comments, but you also get single line comments using `//`. And as in YAML or Front Matter, you can use them only after the code on the line (or on an empty line), not in between.

```scss
/* This is a SCSS file. */

// Heading
h1 {
  font-size: 24px;
}

h2 {
  font-size: 20px; // Set font size
}
```

My favourite use of multi-line comments in SCSS files is to add file description and index.

```scss
/*
* _texts.scss
*
* Definitions of all text elements - headings, paragraphs, links.
* 
* Link styling withing a different element (list, table) is included in the respective files.
* 
* Index
* - Headings
* - Paragraphs
* - Links
* - Links inside text
*
*/

h1 {
  font-size: 24px;
}
```

## Liquid

Liquid only has multi-line comments, defined by `{% comment %}` opening tag and `{% endcomment %}` closing tag. Anything in between will be ignored by Jekyll and not rendered.

```
{% comment %}
This is a comment which will be deleted when Liquid is processed.
{% endcomment %}
```

I don't really like Liquid comments as I can never get Liquid syntax highlighting to work properly and then it would not grey out the Liquid comments, so it looks like normal Liquid code (as you can see in the code snippet above). Instead I use HTML comments which are highlighted/greyed out nicely.

## Markdown

Comments in Markdown files are tricky, because technically Markdown doesn't have comments. There are several workarounds, mainly using Markdown to generate links - empty of failed and not rendered at all, but they all can vary depending on type of Markdown processor you are using and even which version of it.

It would be too extensive to list all the options here, so better check this [post on Stack Overflow][1], discussing it and detailing several possible methods you can choose from.

[1]: https://stackoverflow.com/questions/4823468/comments-in-markdown

When choosing your approach to Markdown comments you also need to take in consideration if the comment will be visible in the rendered HTML code. You can generate an empty link without the comment, but it would still render extra HTML code that is not used on the website. Some methods will also leave the comment in the rendered code, even if not displayed on the page, but still accessible in the HTML code. You should choose a solution that will not clutter your output code and that will keep your comments private.

I think best solution is to use HTML comments - Markdown supports HTML code, you can get HTML comments nicely highlighted/greyed out in your IDE, they are visually significantly different from the rest of the Markdown document for me to quickly spot them and distinguish between comment and content (plain text vs `<!--  -->`), and I can remove them during the rendering process so they stay private only in my source files.

## JavaScript

JavaScript uses only single line comments, similar to SCSS, using `//`. Same rules apply, you can have them only after a code on a line (after semicolon `;`) or on an empty line, not within the code.

```javascript
// Heading
some.javascript(code);

also_some.javascript(code); // This is not really JavaScript code
```

---

## Support me 💓

Did you find it useful? Star this repository and share it with a friend. You can also buy me a coffee. Thank you.

<br>
<a href="https://www.buymeacoffee.com/mareklexuan" target="_blank"><img src="https://cdn.buymeacoffee.com/buttons/v2/default-yellow.png" alt="Buy Me A Coffee" style="height: 53px !important;width: 192px !important;" ></a>
<br>
