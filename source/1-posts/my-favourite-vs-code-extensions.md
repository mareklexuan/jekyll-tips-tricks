# My favourite VS Code extensions

I use VS Code (Visual Studio Code) as my main IDE (integrated development environment), with Github Codespaces as my backup development tool. GitHub Codespaces is just a cloud version of VS Code, so I can have them both set up the same way, using one account, and I can seamlessly switch between them if I need to edit something on the go.

I use several extensions in VS Code, most of which I use to eliminate errors and improve productivity. I don't use anything Jekyll specific as there are plenty of "generic" extensions that can make my work with Jekyll easier and faster.

## Prettier - Code formatter

Classic of classics. One of the most popular VS Code extensions, formatting your code and highlighting its syntax based on the programming language you use. It works great with HTML, CSS, JavaScript, Markdown and YAML.

However it doesn't work with Liquid. There is a plugin for Prettier - [prettier-plugin-liquid][1] - that formats and highlights Liquid as well as HTML code, but I wasn't able to get it working, so I just use it for HTML parts. Also, from the demo it seems like it would highlight Liquid and HTML tags in the same color, which would be pretty confusing to me.

[1]: https://github.com/Shopify/prettier-plugin-liquid

## Tabnine

Tabnine is a code predictive AI-powered extension to help you write your code more efficiently. An AI coding assistant. As you write, it can predict the rest of your code, even whole snippets, and be taught to understand your style.

I only use the free Basic version, which lacks all the advanced features like learning on your code, full code snippets, code explanation, generating tests etc., but I don't really write code regularly, so I wouldn't be able to use all those features anyway.

The free version can still predict the rest of the line when writing a code, complete your HTML tags, add Liquid closing tags etc. And it can also help you with writing content as it can predict the next few words as you write. Even completing the next word is a very useful feature and helps you write your content faster, and with fewer typos.

## Material Icon Theme

Adds icons to the files in your directories based on the format of each file - HTML, CSS, Markdown, images, JavaScript, YAML etc., to help you navigate your folders.

## markdownlint

Linting is automated checking of your code for programmatic and stylistic error; a lint tool is a basic code analyzer. It finds errors, which will most likely not break your code, but are sub-optimal or not according to set language standards.

In Markdown, the lint tool checks if you use Markdown correctly. For example, it warns you that instead of using bold text for headings, you should use actual headings. Or you get a warning if you skip heading level or you use incorrect type of brackets in your links.

It is automatic and notifies you inline, so you don't need to run it to get it to check your code/content. You see the error immediately and you can fix it right away, even before you preview your Markdown content, or worse, before you publish it.

## Code Spell Check

Basic spell check for code and documents. It is a great "first-line defence", before you check your content with something more sophisticated (like a document processor).

## Error Lens

Error lens help you with eliminating small errors and typos in your code. It highlights error like missing brackets or semicolons, extra commas etc. It shows the error inline, as you type, so you don't have to run it to see the errors and be able to fix them.

## Toggle Zen mode

Zen mode removes distractions from the VS Code interface - it hides all tool panels, file explorer etc., darkening and fading everything out, leaving only the content section for you to focus just on writing, no matter if it's the code or text.

I find it the most useful when writing content for my website - blog posts and pages, as I can just focus on writing the content without having to look at all the panels. Especially the file explorer, because then I would start thinking about what file I need to edit, what other content I can add etc. Now I don't see them. Out of sight, out of mind.

## Word Count

Very simple extension that just adds a dynamic word counter, so you don't need to copy your content out to a different tool (like Google Docs or MS Word) to see how long your post is.

It updates automatically as you write, so you also don't need to "request" the calculation by selecting the tool in the panel etc., like it is with classic document processors.

## Color Highlight

Nice extension to highlight your HEX colors - it gives the HEX code background color in the same color. It helps you visualize your colors easier.

## indent-rainbow

Finding related code in the indented large blocks of code can be problematic. This extension adds color bars, connecting code (for example HTML tags) on the same level, so you can easily see the beginning and the end of each element.

## Auto Rename Tag

Very simple extension that helps you automatically rename both HTML tags (opening and closing). I don't get much use out of it, but it occasionally helps if I have a typo in the tag and I need to edit it or when I am changing tags completely.
