# Moving from WordPress to Jekyll

Before Jekyll I pretty much only knew WordPress and online web builders. I knew there were some other tools, usually very enterprise focused, like Kentico, but those were too complex and unreachable for common users.

I have been using WordPress for years, since around version 2.5, almost 20 years ago. Always building some fun websites, small projects, for myself, friends and family, or even small jobs. Recently I also worked as a freelance web developer and project manager, building more websites.

And I like WordPress. I like the ecosystem and its size. To be able to customize the web builder with plugins and themes to do what you want and look how you want it, that sounded like a dream. But the more I dove into it over the years, the more I learned about it, the more I understood the complexities and risks it introduces - performance, security, and maintenance - for both the tool and the website.

It was fine for others, most people didn't care that much about it beyond the basics, or didn't really understand it, but for my website, simple personal website with a blog, managed by only me, which I was working on every day and had to take care of every day, many things started frustrating me about WordPress and I started looking for new platform to replace it.

## Jekyll entering chat

I was introduced to Jekyll at work. The company I worked for used to create a marketing website to promote their product (Saas marketing platform), the company, and to create a blog and public online academy in their marketing field. Looking back and comparing it with my website, it was very complex with a lot of custom pieces, but the core idea was there and is the same.

I was immediately amazed by the simplicity of Jekyll and static site generators in general. Being able to create a website just from a few files, having everything is a simple folder structure, being able to create templates of the website with a few lines of code, or using text files to create a basic database.

Compared to Jekyll, WordPress looks like a huge monster. And it kinda is. Due to its size and complexity, WordPress was slowing me down and distracting me from what I wanted to do, write a blog and create content, so I decided to switch. I love building and tinkering, and I wanted to learn a new thing in the process, so Jekyll showed me the perfect opportunity.

## The comparison

I understand that I am comparing two different approaches, dynamic CMS and static site generator, and what frustrates one person somebody else can consider as a great feature, but the base goal of both tools is the same - create and maintain a website.

I know it isn't binary, it isn't black and white, and there are many nuances to every problem and small solutions and arguments and counterarguments. One might be better now, but does it have a future? Is a more complex tool with more moving parts, but a more updated and bigger community better than older, slower paced tools where you need to often create your own solutions?

And I get that there may have been solutions to my challenges in WordPress but I wasn’t aware of them or they were not good enough. And that's what it's all about - to find a tool that suits my style, my thinking and my routine. Something that suits me now and will suit me for some foreseeable future.

With Jekyll, I can focus more on my main goal - writing content, even offline, instead of constantly maintaining the website; and I can make a faster loading website that can't be hacked. It does require more work and is for tech savvy users, but I am also getting new skills and more experience with it.

- **Tracking changes and history** - WordPress only tracks history for posts and pages, but it slows it down (WordPress and your website). With Jekyll, I can use GitHub (that is outside of the Jekyll and web hosting server) to track all changes in detail.
- **Writing content** - Jekyll supports Markdown, which is much quicker than formatting text with WUSIWUG.
- **Local editing** - With Jekyll you build it all locally. With WordPress you need to set up your local environment, which is not as simple as it seems and often behaves differently than a live site.
- **Offline editing** - As I have everything in Jekyll locally, I can also work offline and commit my changes once I go offline. With WordPress, you need to download your whole website before you go offline.
- **Community** - WordPress community is no longer supportive. There is a lot of ego from more advanced users, looking down on beginners. Even local meetups felt like Game of Thrones, people fighting to control the groups to sell their services.
- **Maintenance** - Active WordPress plugins get regular updates, which is great, but when you have a few plugins, you need to test and update your site almost daily. Often just to patch bugs and exploits.
- **Performance - generating pages** - Jekyll generates the whole website at once and then I can host it on my server. No need to generate every page every time somebody accesses it, or create some workarounds.
- **Performance - code bloat** - With Jekyll I have full control over what I add to my website. WordPress with plugins add unnecessary code that you need to optimize.

_More details breakdown of the reasons why I decided to leave WordPress and move to Jekyll is [here](https://github.com/mareklexuan/jekyll-tips-tricks/blob/main/posts/reasons-why-i-chose-jekyll-over-wordpress.md)._

## Did I make the right choice?

Was it a great decision in the short term? No. I had to learn so many new things and it took me forever to put together the first usable version of my website, which is still much worse from a visual perspective than what I could have done in WordPress within one afternoon.

My hope is that in the long run it will pay for itself, that the time and frustration from managing WordPress site I can invest into learning new skills and building my website exactly how I wanted, faster and better optimized, and allow me to focus on the primary goal - writing the content.

It all comes down to your needs. I think WordPress is more suited for casual users who are not tech savvy and need a simple interface to add and manage the content and media. But they will probably prefer some online builder, where they don't need to take care of the maintenance of the tool, security, performance etc.

WordPress is also suited for e-commerce, membership sites, closed communities etc., as such features are not possible on Jekyll. But for a simple website, for tech savvy users who don't mind tinkering and writing their own code, static site generators are a great option.

Is Jekyll the best choice? It depends. There are already better and faster tools, but often still in development. Jekyll is a bit older and past its hype phase, but it works, it is stable and still has a good community around it. Down the road I might change my mind and switch to something else. If it would cover my then needs butter, why now.

I might even come back to WordPress one day and use it again, but probably only if I want to build something more complex, something I wouldn't be able to do on a static site. But that day hasn't come yet.
