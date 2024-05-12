# What are Ruby gems

Ruby gems are basically plugins, adding a specific function to your Ruby distribution. Jekyll is technically also a gem, it is not a stand alone program. And most of the Jekyll plugins and themes will also be available in the form of a Ruby gem.

As they are all part of one "system" (your Ruby installation), they might have dependencies on other gems to run. The most obvious example are Jekyll plugins - you can't run Jekyll plugins without Jekyll. But most of the gems will have specific requirements for a version of the needed gem - for example that it would require Jekyll 2.5 or newer to run.

To make sure everything in your Ruby installation runs correctly, you need to maintain your gems and the dependencies. To keep them updated. Check for updates every time you start working on your Jekyll project or every time a new version of any gem is released.

Some users take a different approach and they update their gems only when they have to, only when something starts to break, not to waste time by testing and updating each gem every time a new version is released.

I am not going to tell you which approach is better. I am not that knowledgeable about Ruby to be able to tell you what are the risks of each approach. It will also depend on your conditions, your setup and your workflow. For example, if you are using Jekyll for GitHub pages, you are limited by the [dependencies set by GitHub pages](https://pages.github.com/versions/).

I adapted my approach to be a balance of both worlds - I don't like the maintenance and want to update anything as little as possible, but I also want to keep things running smoothly and securely. So I try to pick my updated and update only when it is really necessary:

**1. I subscribe for the new release of my main components.** - Jekyll and plugins I use. Every time the new version is released, I get a notification and I check what is included in the new version, to decide if I should update it.

- If it's a security or a bug release, I always update it. There is no reason to hold such an update.
- If it's a feature release, I need to think if it is going to break something. New features in Jekyll plugins and other gems are usually safe, but new versions of Jekyll, especially a major release, can often break your project as the plugins are not adapted to it yet. So it might be smart to wait a few weeks for the plugins to catch up and only then update Jekyll as well.

**2. From time to time, I check if any of my Ruby gems are outdated.** - I only set notifications about Jekyll and Jekyll plugins I use. For other gems, I simply check if they are in their latest version. I don't do it regularly, daily or every time I run Jekyll, but that's because I keep forgetting about it, not because I would think it is not necessary.

- I would make a list of outdated gems maybe every two weeks or so, mainly because I don't use Jekyll that often and I keep forgetting to check for them. If I see any gem that needs updating, I would look up it's changelog to see if it's safe to update, using the same logic as above - if it's bug or security update, I would update it immediately; if it's feature update, I would investigate further and then decide if it's safe for my setup to update it. You can search for any Ruby gem and its changelog at <https://rubygems.org/>

But you do you. Do your update routine every time you work on your Jekyll project, or update gems only when things break.

## Terminal commands to manage your Ruby gems

Here are several most useful commands to manage your Ruby gems.

Full list of _gem_ commands, with detailed specification, can be found here: <https://guides.rubygems.org/command-reference/>.

### Install gem

Install specific gem (replace GEMNAME with name of the gem you want to install - see <https://rubygems.org/> for list of available gems)

```terminal
gem install GEMNAME
```

For example:

```terminal
gem install jekyll-feed
```

Install specific version of the gem

```terminal
gem install GEMNAME -v VERSION
```

For example:

```terminal
gem install jekyll-feed -v 0.17.0
```

If the version information is not included, the latest version of the gem will be installed.

### List all local gems

Display list of all installed local gems.

```terminal
gem list
```

### List all outdated gems

Display the list of your outdated gems, with your version and what is the latest version.

```terminal
gem outdated
```

Output can look like

```terminal
bundler (2.5.9 < 2.5.10)
```

### Update gem

Update specific gem

```terminal
gem update GEMNAME
```

### Uninstall gem

Uninstall specific gem

```terminal
gem uninstall GEMNAME
```

## Don't forget to update your Ruby version

One big dependency is the gem's requirements of the Ruby version. The new version of gem can bump up the requirement to a higher version of Ruby, so you also need to update it from time to time. Understanding Ruby versions is a problem of its own, which I have covered in [this post][1].

[1]: https://github.com/mareklexuan/jekyll-tips-tricks/blob/main/source/2-tips-and-tricks/understanding-ruby-and-jekyll-versions.md

## Updates can solve your problem

Updates are not only about fixing bugs, vulnerabilities, or adding more features. Often we fall to the illusion that adding new features is about adding something new, something we don't use yet. But it can often be just a support for what we are already trying to do. Sometimes updates enhance features you already use and that can solve some of the problems you have.

It happened to me as well. In one instance, when I was reworking CSS to SCSS, I couldn't get it run properly, according to the official documentation, only to realise after several hours of debugging that I have an outdated version of Jekyll that didn't support the functions I was trying to use. All I had to do was update Jekyll and a Sass converter and everything worked perfectly.

So make sure that you check your updates at least from time to time, and if you postpone some of the updates, don't forget about them. Otherwise they might give you a headache down the road.
