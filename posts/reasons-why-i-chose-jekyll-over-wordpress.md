# Reasons why I chose Jekyll over WordPress

This is a follow up on my post [Moving from WordPress to Jekyll](https://github.com/mareklexuan/jekyll-tips-tricks/blob/main/posts/moving-from-wordpress-to-jekyll.md), a more detailed breakdown of reasons why I decided to leave WordPress and move to Jekyll.

Just to set the scene:

I was no longer making websites in volume. I was building only one, my personal website, a simple presentation with a blog, and I was the only person building it, maintaining it, and writing all the content. I didn't need to worry about multiple people editing it at the same time etc.

I am also using GitHub (obviously, as we are on GitHub right now), mainly as a way to track history and changes of all files. But if you are using a different service, it will work the same as it is about the git itself.

And I am doing everything locally on my computer (or in GitHub Codespaces). I am not building my website virtually in Docker somewhere or using any automated deployment. Well, I used to but that no longer supports my version of Jekyll, so now I am just uploading files to FTP manually. It'S very basic and manual, but only takes a few seconds.

## Writing content

**WordPress**

WordPress uses WYSIWYG. In essence, WYSIWYG is a great idea - you can immediately see what the result will look like. But it is slow. You need to write the content and when you want to format/style something, you have to highlight it and then click the button with desired format/style. For every heading, link, list and so on.

WYSIWYG is great for the average user, but not for somebody who doesn't want to be distracted by constant switching between writing and formatting. It also often created unexpected results, adding spaces, empty lines, margins etc., as there could be something in the theme or some plugin influencing it.

You could edit your content in HTML code, but that isn't perfect either, because your theme or plugins in WordPress could be adding their own HTML tags, and it sometimes creates very unexpected results that you need to debug and fix.

And it's all after you open your login page, log in, and find and open the correct page. Every time you want to update something. That is too many steps to add a missing comma.

**Jekyll**

Jekyll uses Markdown. You write everything in a text format, add simple markup and then Jekyll processes it and adds necessary HTML tags. It is much faster as you can just write a few symbols to the text and you are set, and it guarantees consistent output.

You also don't need to login anywhere, I can do everything from one local application. I can open my customized IDE (I am using VS Code), open the file you want to change and start writing. It is much more straightforward and without any distractions.

## Tracking changes and history

**WordPress**

In WordPress you can track changes for posts and pages, but each change, even a simple typo, creates a copy of the page in the database. And if you do a lot of changes (tweaking content often, updating it regularly), or simply over time, you would collect a lot of historical records which would start filling up your database and then slowing down your website. You would have to sacrifice loading speed (both of the tools and the website) for page history and that is not a great tradeoff.

To get around that, I started using GitHub to store my content and track changes, and stopped using the history in WordPress to speed it up. But that created additional work for me, as I had to first write the updated content and commit it to GitHub, and then login into Wordpress, find the correct page, update it and publish it to my site. That is a lot of hoops I had to jump through just to fix a typo.

And that's just for the content. If you change something in a template (theme), in settings, or in a code, you don't have any records of it in WordPress. There are some plugins that can track that, but often to a limited extent and it is just adding more moving parts that can break for a simple feature.

Today there are perhaps tools that can save your WordPress installation to GitHub and use it to track the history, but then you would have information in two places - something in GitHub and something in the database. And it wouldn't record information about where in the WordPress's CMS UI the change was done.

**Jekyll**

With Jekyll you use GitHub as standard, and GitHub's (git's) purpose is to track changes and history. You have your GitHub repository and continuously add to it, like developing any other program/source code. Technically your could probably have everything only on your computer and never save it to GitHub, but than isn't a standard flow, and you are adding extra complexity to a very simple process.

Jekyll has a small and simple structure of templates and data files in a few directories, which can even be customized. Also, you don't need to go through source files of Jekyll itself when checking the history of some page, only the source code of your website. Automatic tracking and simple management.

## Local and offline editing

**WordPress**

To edit locally on WordPress, you need to set up your local environment which was not a simple task and it was often unreliable as it was difficult to rebuild the same environment as you have on the server. Often there were mismatches in versions of PHP and MySQL, and your local website would behave differently than your live version, so you couldn't trust your local results.

To work on WordPress locally also means that you need to download your whole WordPress installation, as the whole program is hosted on your website, every time you want to do some change. And that can be a sizable download and it slows you down as you need to wait for it to download to start working on it.

And to work offline, you need to prepare for it, you will always need to download your entire WordPress installation to your computer. And if something on your website changes in the meantime, your offline edits might not work the way you would expect.

**Jekyll**

Jekyll runs locally by default. You have three components - Jekyll, your source code, and your generated website code. Jekyll (as an application) is only in your computer, compared to WordPress you don't upload it to your website. Then you have your source code - structure, data, rules and templates - from which your website code is generated. Source code is stored on your computer and GitHub.

You still need to set it up to run it on your computer, but the process is much simpler and consistent, even on a computer without any programming tools.

And as you are local by default, you are offline by default as well. As your website is static and can't change unless you change it, you don't need to worry about constantly downloading it to your computer. It works the opposite way, it changes only when you change it. Sp you can work on your project offline, keeping all changes only on your computer, and publish it later (both source code and website code).

\*_Technically the source code is stored on GitHub and you download it to your computer, but if you are the only person working on it, you don't need to sync your files. If more people work on your project, they you need to sync them, but it takes only a few seconds as you download only new and updated files, not whole website._

## Community

**WordPress**

I stopped enjoying the WordPress community. I felt like it lost the "community" aspect. There is a lot of each between users, seeing each other as competition, and advanced users looking down on beginners. Even local meetups sometimes felt like Game of Thrones, people fighting to control the groups for reputation and to sell their services.

**Jekyll**

Jekyll's community is much much smaller than WordPress’s and not as active, but I haven't encountered any issues. Maybe because the small community is, the more they realize they need to help each other. If nothing more, at least it isn't toxic.

## Maintenance

**WordPress**

WordPress has many moving parts - starting from PHP and MySQL, dynamic page generation and its main components, third-party plugins. All those aspects need to be monitored, managed and maintained. Especially plugins, because they often have bugs or vulnerabilities. They do receive updates regularly, at the popular ones, which is great, but it also means that once you have a few plugins, you are constantly updating them.

Updating plugins is not just clicking a button and waiting for it to download. You need to test it because often they can break your website. And that means to download your website to the local environment, test the update, and then update your website. It's a lot of steps and takes some time. I had around 10 plugins on my website and I received so many updates that I had to do this every other day.

**Jekyll**

You are building a static website, not dynamic, so you don't need that many functionalities like you would need on WordPress. Of course even Jekyll has updates and plugins (to add some Jekyll functionality), but Jekyll is a mature product and well tested, so you get updates only every few months. And I can spend some time once or twice a year to read a changelog and see if I need to do some testing.

You are also updating Jekyll only, a program that runs on your computer, not your website, so you don't need to worry about breaking it. Or about vulnerabilities. And if the new version of Jekyll would break your compilation process, or you can always just revert back to the old version.

_I personally never had any issue while updating Jekyll or any of its components. The only issue I had was automatic deployment which doesn't support newer versions of Jekyll, so I had to turn it off. But that isn't project critical, I can still deploy my website manually._

## Performance - generating pages

**WordPress**

WordPress uses dynamic page generation from a database. Each individual website page is generated the moment you access it, giving you the latest version of that page. That is great for a website that changes a lot, has personalization for users or needs some advanced features, like e-commerce or membership sites, but it is excessive for a blog that usually changes only when you publish a new post.

WordPress needs to connect to the database and run to generate that page, and that takes time. Time it takes the page to load. Jekyll (and other static site generators) on the other hand generate it once and those generated files are stored on your server and served to the visitors, which is much faster as there is no need for any process to run.

That is the main technical difference between WordPress and static site generators. And that is where they get their name from. You generate static pages and serve them directly, opposite to the dynamic pages generated by WordPress. Today there are tools to narrow the gap and give you almost the same functionality on WordPress as well, but still it is another tool you need to manage and maintain, and often pay for.

**Jekyll**

With Jekyll, I generate my website locally on my computer while I am working on it and testing it, and then upload the files to the server. Quick and simple.

## Performance - code bloat

**WordPress**

WordPress is trying to be an universal tool for any website, which often means it (and its plugins) need to have features and functions to cover all needs of all users. That adds extra code and scripts to your website that need to load too when a user loads the website, even if they are not going to use that feature.

Again, there are tools and plugins that can help you limit it, but they are never perfect, can often break your website and they can disable also features you need (as all that code can be in one file, but you need only part of it), and again, adding another thing to worry about and often pay for.

**Jekyll**

With Jekyll I have full control over what is added to my website, even though it also means I have to add it and I can't just use a ready-made solution. But what you lose in extra work, you gain with faster websites and better SEO, and that is a good tradeoff.

## Security

**WordPress**

I never knew how much Internet traffic is just bots trying to hack websites until I became fairly knowledgeable about WordPress and discovered security plugins, which log all attempted attacks. Even freshly published websites can start to get attacked several times a day.

WordPress uses a database to store all data, posts, comments, but also information about the users, including their email address and password. And hackers are trying to get access to your website to get that personal information, or to inject some code/content to your website, usually to add links (affiliate or backlinks to their website), or change your content to display what they want, often turning your website into marketing their product/service/website.

And because WordPress powers over 40% of all websites, every WordPress website has the default login page the same (the URL), and is used by non-tech users who also don't have enough knowledge about online security, which makes WordPress perfect target for the hackers.

**Jekyll**

But with static websites, there is nothing to hack. Your website is not connected to any database from which it takes the data and there is no login page to attack. All that is out there is all what is.
