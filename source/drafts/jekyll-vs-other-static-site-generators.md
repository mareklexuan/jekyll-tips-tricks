# Jekyll vs other static site generators

Even though this content is dedicated to Jekyll, we should keep in mind it is not the only static site generator out there and it might not be the best tool for you.

There are many static site generators to choose from. Some simple and general, some focused on specific types of the websites (documentation, photography portfolio, CV etc.), some go even further and have app-like frameworks and server-side rendering. For most you don't need to know any programming language, but it helps if you want to create your own custom features and plugins.

Every site generator, even dynamic ones, are in essence doing the same thing. They have the same base logic - they generate HTML pages from your content and your template. How they achieve it and what you need to do to create those source content and template files, is what sets them apart.

When selecting a tool for you, or when thinking switching, I always consider these parameters:

- **My needs/use-case** - How will I use it? Am I building a few sites for fun, or am I making a new page every week for a client? Do I need specific features or am I fine with generic tools? - I now only have one project, one simple blog website, so I don't need anything complex. And I am just starting, so first I need to learn more about websites, web design, and web development, before I would need something more complex.
- **Ease of use** - How easy is it to use it? How many people have to learn to use it, especially non-developers? One thing is you learning the tool, but what if you need others to use it and edit the websites as well? - Only I work on my projects, so I don't need to worry about training others to use it. But in my previous job we used Jekyll and we had about 10 people editing it, mostly updating the content. I, for example, had to learn not only to use Jekyll, but also to work with git, GitHub and an IDE, or even Markdown properly, to be able to update the company's website.
- **Languages** - What programming languages do I already know and I want to use? Is there something I want to learn? - I don't know anything and I don't want to learn anything. I wanted a simple project, easy to set up, easy to manage. Only languages I wanted to learn were HTML and CSS, as knowledge of those can be used in other jobs and industries, like marketing (SEO etc.) But If you already know some programming languages, perhaps you should start your selection from those tools written in the same language, so you can easily use them or even modify them.
- **Project's maturity** - In what phase of the development is the tool? Is it still early, getting updated constantly, or is it "done" and doesn't change as often? - I like tools that do what I need and don't constantly sweep the rug under my feet. I hate constant maintenance and need to rework my projects just to update the tools.
- **Existing content and documentation** - How extensive is the tools documentation? Does it cover only the basics, or advanced uses as well? How easy is it to read? And what other content by other users is out there? Is it up to date? Are they just basic tutorials, or complex applications? - Obviously, extensive documentation is the way to go. However, some are hard to navigate through and to understand, which really slows you down.

Always start from defining your needs. What do you want to build and how do you want to use it. There are many tools, some will look very attractive with their claims, especially about compiling speed, but do you really need them? Aren't they too complex for you? Can you still keep focus on actually building the website and writing the content, when constantly thinking about updates?

## Popular static site generators

Here are some examples of the most popular static site generators. Whatever you want to build, you can probably do anything and everything with any of those tools, but each of them will have a different approach and set of features to do that.

### Jekyll

- Build with: `Ruby`
- Template language: `Liquid`
- Website: <https://jekyllrb.com/>
- Repository: <https://github.com/jekyll/jekyll>

Jekyll is a blog-aware static site generator, developed to create simple blogs and pages, as an alternative to WordPress. It uses Markdown to store the content of the pages, Liquid to create templates, and YAML for data and settings. It rose to popularity as it was selected as a compiler for GitHub pages.

It is a mature and stable project, very simple to use and to learn, even for non-dev beginners like me. It is great for learning basic logic of web development and static site generators. It can build large and complex sites, but I think its great strength is for people who want to build a small website or two, personal projects, who update it occasionally, write a few posts every now and then, and who don'T want to learn a lot of programming.

Examples of Front Matter (_taken from: <https://jekyllrb.com/>_):

```Front Matter
---
layout: post
title: Blogging Like a Hacker
---
```

Examples of Liquid templating (_taken from: <https://jekyllrb.com/> and <https://shopify.github.io/liquid/>_):

```liquid
{% if customer.name == "kevin" %}
  Hey Kevin!
{% elsif customer.name == "anonymous" %}
  Hey Anonymous!
{% else %}
  Hi Stranger!
{% endif %}

<p>{{ page.date }} - Written by {{ page.author }}</p>
{{ content }}

[Link to a page]({% link news/index.html %})
[Link to a file]({% link /assets/files/doc.pdf %})
```

Example of YAML data file (_taken from: <https://jekyllrb.com/>_):

```yaml
username: jekyll
name: Jekyll
members:
  - name: Tom Preston-Werner
    github: mojombo

  - name: Parker Moore
    github: parkr
```

### Eleventy

- Build with: `Javascript (Node.js 14)`.
- Template language: `Liquid`, `Mustache`, `Nunjucks`, `EJS`,`Handlebars`, `HAML`, `Pug`
- Website: <https://www.11ty.dev/>
- Repository: <https://github.com/11ty/eleventy>

Eleventy is the biggest and closest competitor to Jekyll, and even presents itself as an alternative to Jekyll. It also supports Liquid as a templating language, but you can use several other templating languages too. This gives you much more flexibility of achieving your goals - if you can't do it in one language, try another.

Having support for multiple templating languages is an interesting choice. For a beginner like me, it might complicate things as I would start learning more new things instead of focusing on actually building content for my website, but having alternatives gives a solid future proofing.

In comparison with other static site generators, Eleventy is a fairly young tool. It started in 2018, launching its 1.0.0 version in 2022, now being on version 2.0.1 and already testing 3.0.0. One thing I do like about updating Eleventy is that it has a dedicated plugin to evaluate if you need to worry about breaking changes in your project.

What I don't like is their documentation. It is hard to read and hard to get simple information about how the tool works, how to set it up etc. It is something to consider, especially if you are starting up and you are not as web development savvy.

### Hugo

- Build with: `Go`
- Template language: `Go`
- Website: <https://gohugo.io/>
- Repository: <https://github.com/gohugoio/hugo>

Hugo is known to be the fastest static site generator. It renders complete sites, even large and complex projects, within seconds, often even faster.

When I first looked at Hugo, it seemed to me like a very new tool, as its version was lower than 1.0.0, which would indicate to me it's still in a beta phase. But when you look at it closely, yes, it is still in version v0.y, but it is currently at version v0.125.7, which means it had a lot of development done with over 120 significant (feature) changes. And if you look at its history, you will find out it started in 2013 (first public release).

And it still receives updates, once or twice a week. On one hand it is great, it means the project is growing and moving forward, but it is not what I would like to have. I prefer mature and stable projects, something you need to update only every few months, not all the time. That is the main reason I left WordPress, to avoid constant maintenance. It is also one of the reasons I like Jekyll, not having to worry about updating it.

Even though it is fast, Hugo is too complicated for my liking. I am biassed towards Jekyll as I learned to use it at work, but templating with Liquid is much simpler than how Hugo handles it. It is also a main reason many people are leaving Hugo and coming (back) to Jekyll, despite its performance. Or why some prefer Eleventy, as it is much closer to Jekyll, yet much faster, almost catching up to Hugo.

Examples of Hugo templating (_taken from <https://gohugo.io/templates/introduction/>_):

```go
{{ $v1 := 6 }}
{{ $v2 := 7 }}
<p>The product of {{ $v1 }} and {{ $v2 }} is {{ mul $v1 $v2 }}.</p>

{{ $convertToLower := true }}
{{ if $convertToLower }}
  <h2>{{ strings.ToLower .Title }}</h2>
{{ end }}

{{ $s := slice "foo" "bar" "baz" }}
{{ range $s }}
  <p>{{ . }}</p>
{{ else }}
  <p>The collection is empty</p>
{{ end }}

```

### Next.js

- Build with: `JavaScript`
- Template language: `React`
- Website: <https://nextjs.org/>
- Repository: <https://github.com/vercel/next.js>

Next.js is an app-like SSG framework, combining static site generation and server-side rendering. It is aimed for more advanced developers who want to build not only static websites, but whole web applications.

### Gatsby

- Build with: `JavaScript`
- Template language: `React`
- Website: <https://www.gatsbyjs.com/>
- Repository: <https://github.com/gatsbyjs/gatsby>

Gatsby is a similar type of tool as Next.js. It is also a React based framework for developing web applications.

Both tools (Next.js and Gatsby) are much more complex that simple static site generators like Jekyll. And to be honest, I can't tell you the difference between these two, as it is way above my skill level.

## Will I switch?

No, I am not planning to leave Jekyll. I am happy with it. I like its simplicity with Front Matter, Markdown, Liquid and YAML. I like its documentation, which was very clear to read and follow when I was starting up. I keep coming back to it and I can always easily find what I am looking for.

I am far from being slowed down by Jekyll. My website is still very small, I only have a few pages and even if I start adding more content, it will take a very long time before it will become a problem. There are also ways to speed up build time of Jekyll, so the migration to another tool is not the only option.

And I don't really want to learn a new tool. It took me a lot of effort to learn to use Jekyll and build my website, so now I just want to build the content, not constantly tinker with some code. Only when it comes to the design.

Considering how much effort I would have to put into learning a new tool, studying new documentation, and then migrating the project, would migration still make sense? How much time would I actually save with faster build speed? Will it ever "pay back"?

But your mileage may vary. You always need to evaluate your use-case before you jump to any conclusion. You might (and probably will) have different needs - for your projects and for your skill development. Is it really worth it, learning a new tool and language to save a few seconds (or even minutes)?
