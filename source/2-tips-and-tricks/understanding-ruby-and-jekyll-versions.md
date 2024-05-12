# Understanding Ruby and Jekyll versions

Every project might have different approach to version numbering and how many versions/branches of the project they maintain, but standard numbering system is `x.y.z`, where:

- `x` - major version - big release, usually rework of the tool, new technologies etc. (often introducing breaking changes - new version can break your project = you need to adapt your project to the new version)
- `y` - feature version - adding new features (expanding the major version, sometimes can introduce breaking changes)
- `z` - bug and security updates

## Ruby

Usually the new version of a program replaces the older version, progressing linearly - version 3.9.2 replaces 3.9.1 and version 4.0.0 would replace anything 3.y.z. However, some projects maintain multiple branches, to ensure better compatibility for its users, as often even feature versions can introduce breaking changes.

Ruby is using the multi-branch approach. It supports 4 feature versions, to make sure your project does not break every few months due to the new feature release. So you can keep using your version of Ruby, only update the fixes, but don't update to the new feature version, which could compromise your project and force you to rework it just to update your Ruby environment. Think of this as every version has one extra feature compared to the previous one, unless we are moving up a major version (for example going from Ruby 2.x to 3.x).

Ruby development runs on a predefined cycle schedule. For transparency, every cycle starts on the same date (December 25th) and has the same length, therefore you know what you can expect in terms of support and updates.

Support for every version/branch has two phases - normal maintenance for bug and security fixes, and security maintenance for security fixes only. Once it reaches its end-of-life (end of security maintenance period), the branch is no longer maintained.

For example, Ruby version 3.0:

- Release date: 2020-12-25
- Normal maintenance: 2023-04-01
- End of life: 2024-04-23

It is a little confusing at first, as it can often mean that on the same day you can get an update for 4 different versions of Ruby. For example, on 23 April 2024 there were releases of versions 3.0.7, 3.1.5, 3.2.4 and 3.3.1, all fixing the same issue. But it becomes much more understandable when displayed on a timeline:

![Ruby release cycles timeline](https://github.com/mareklexuan/jekyll-tips-tricks/blob/main/source/media/ruby-cycles-timeline.png)

_Taken from <https://www.ruby-lang.org/en/downloads/branches/>_

So don't take the update of your Ruby lightly. Make sure Jekyll and its dependencies (mainly plugins) support the new Ruby version, or that you upgrade them before you upgrade the whole Ruby installation. And keep your Ruby version updated and update your Ruby version before it reaches the end of life, or even the security maintenance phase, so you don’t use a version with possible vulnerabilities.

In the 3 years I have been learning and working with Jekyll, I have upgraded Ruby only once, from 2.7.4 to 3.2.3. I had some problems updating several Ruby gems (maybe even Jekyll itself) and it turned out it was because I had an old version of Ruby, which also was no longer supported (it was after its end of life). So the newer version of Ruby was a dependency for some of the Jekyll components I have been trying to use.

However, I didn't go straight to the newest version of Ruby. I selected the Ruby one feature version lower, because I didn't need the newest version, and I also wanted a version with several fixes already implemented, not something too fresh. It was also an officially recommended Ruby version, probably for exactly the same reason.

## Jekyll

Jekyll also has a slightly different approach to releasing new versions. It follows the standard version numbering system explained in the beginning, but it also maintains multiple branches like Ruby, to ensure more compatibility. Jekyll currently has two branches, Jekyll 3 and Jekyll 4, with latest versions 3.9.5 and 4.3.3.

The reason to maintain multiple branches is most likely influenced by its primary purpose - to power GitHub Pages. GitHub Pages take their time to update the dependencies to newer versions of Jekyll (or any other Ruby gem), so it wouldn't break pages of its users. Therefore Jekyll still maintains the major/feature version of Jekyll that is used on GitHub pages, to provide at least bug fixes.

But there are still users who want to push the tool forward and are open to having a new version, even if it means reworking their projects with the newly released version. And for those users we have the second branch, currently version 4.3.3 and already working on 4.4.0 (and discussing a new major version 5.0.0).

I am not sure if the Jekyll team would be willing to maintain three branches (with Jekyll version 5). I think it will wait until GitHub Pages adopts the newer version of Jekyll, making Jekyll 3 obsolete and moving primary focus on Jekyll 5 and having Jekyll 4 as a secondary branch to maintain and provide fixes only, for GitHub Pages again.

But for now, we have Jekyll 3.9 and Jekyll 4.3. So if you are starting and you don't want to use Github Pages, go for the newest version of Jekyll available.
