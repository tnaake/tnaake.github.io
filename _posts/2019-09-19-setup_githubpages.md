---
title: "How I setup my GitHub Pages site" 
date: 2019-09-19
tags: [website, github]
header: 
  # image: "/images/"
excerpt: "How I setup my GitHub Pages site"
comments_id: 1
---

Today I set up for the first time my GitHub pages site. As a documentation I 
will describe here how I set up this website. 

# Start

* go to 
[https://mmistakes.github.io/minimal-mistakes-jekyll](https://mmistakes.github.io/minimal-mistakes-jekyll)
* clone the repository to my `Projects/` folder 
```sh
git clone https://github.com/mmistakes/minimal-mistakes.git
```
* remove unnecessary files by entering after navigating to the cloned directory
```sh 
rm .editorconfig
rm .gitattributes
rm CHANGELOG.md
rm minimal-mistakes-jekyll.gemspec
rm README.md
rm screenshot*
rm -drf .github
rm -drf docs/
rm -drf test/
```
* rename the directory to `tnaake.github.io`
* create a new new repository with the name `tnaake.github.io` on GitHub
* push the existing repository from the command line to GitHub
```sh
git remote add origin https://github.com/tnaake/tnaake.github.io.git
git push -u origin master
```

After this you can push the changes to GitHub. 

# Configuration

## _config.yml 
The first thing I did was editing the `_config.yml` file. This file is one of the 
most important files to configure the contents of the site. 

Open the `_config.yml` file in your favourite editor and edit the the following entries: 
* `locale: "en-GB"` 
* `title: "~/"`, the title will be the name of the starting page
* `name: "Thomas Naake"`
* `description: "Thomas Naake's GitHub pages site"`
* I created a directory `images/` and copied a picture there. In the author 
section under avatar, I included the relative path of the picture. This will 
add the picture to the sidebar.
* `bio`: enter here a descriptive bio enclosed by ""
* set `location`
* enter username for some social media accounts (e.g. GitHub, Twitter) under 
Site Author and Site Footer

In the default section, there is an entry for _posts. I also put some settings 
for _pages (e.g. for the `About` page. 
I entered the following to the `Defaults` section

```markdown
  # _pages
  - scope: 
      path: ""
      type: pages
    values: 
      layout: single
      author_profile: true
      comments: false
```

## pages
Next, I created a `_pages` directory in `tnaake.github.io` directory that 
will host more contents of the site. I added a `about.md` file in the `_pages` 
with the header 

```
---
permalink: /about/
title: "About the author"
modified: 2019-09-19
comments: false
author_profile: true
header:
   #overlay_image: /images/slide-code2.png
   #overlay_filter: 0.3
---
```

directly followed by 
<pre class="prettyprint pre-scrollable"><code>
&lbrace;% include toc %&rbrace;
</code></pre>


to include a table of contents for navigation. 

Subsequently, I added to this file information on CV, Research, Publications, Software, 
Talks and Posters. 


## posts 
I added a `posts.html` file in the `_pages` directory with the following 
contents

```
---
layout: archive
permalink: /posts/
title: "Posts"
modified: 2019-09-19
comments: false
author_profile: true
header:
  #overlay_image: /images/slide-code2.png
  #overlay_filter: 0.3
---
```

I added furthermore the following lines of code to the same document:
<pre class="prettyprint pre-scrollable"><code>
&lbrace;% capture written_year %&rbrace;'None'&lbrace;% endcapture %&rbrace;
&lbrace;% for post in site.posts %&rbrace;
  &lbrace;% capture year % &rbrace;&lbrace;&lbrace; post.date | date: '%Y' &rbrace;&rbrace;&lbrace;% endcapture %&rbrace;
  &lbrace;% if year != written_year %&rbrace;
    &lt;h2 id="&lbrace;&lbrace; year | slugify &rbrace;&rbrace;" class="archive__subtitle"&gt;&lbrace;&lbrace; year &rbrace;&rbrace;&lt;/h2&gt;
    &lbrace;% capture written_year %&rbrace;&lbrace;&lbrace; year &rbrace;&rbrace;&lbrace;% endcapture %&rbrace;
  &lbrace;% endif %&rbrace;
  &lbrace;% include archive-single.html %&rbrace;
&lbrace;% endfor %&rbrace;
</code></pre>




To create the first post (this post), I created a directory `_posts` in 
`tnaake.github.io`. Within `_posts` I deployed the first post in markdown
language. Make sure to name the file in the `yyyy-mm--dd` format.

## navigation.yml
To set up the navigation bar, I put the following contents in `navigation.yml` 
that is located in the `_data` directory: 

```markdown
# main links
main:
  - title: "About"
    url: /about/
  - title: "Posts"
    url: /posts/
  - title: "Tags"
    url: /tags/
```

# Build locally a version of the site

To do some testing, before pushing to GitHub, it is recommended to build and 
test locally the site. 

1. `install ruby2.5-dev`{:.sh} 
2. `sudo bundle install`{:.sh} 
3. `bundle install`{:.sh} 
4. `bundle exec jekyll serve`{:.sh} 

<section class="single">

	<div class="wrap">

		{% if page.comments_id %}
			{% include comments_post.html %}
		{% endif %}
	</div>

</section>

