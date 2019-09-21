---
title: "How I setup my GitHub Pages site" 
date: 2019-09-19
tags: [website, github]
header: 
  # image: "/images/"
excerpt: "How I setup my GitHub Pages site"
---

# Start

* go to [https://mmistakes.github.io/minimal-mistakes-jekyll](https://mmistakes.github.io/minimal-mistakes-jekyll)
* fork the repository and rename it to 'tnaake.github.io' 
* clone the repository
* remove the files by entering after navigating to the cloned 
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

After this you can push the changes to GitHub. 

# Configuration

Open the '_config.yml' file in your favourite editor and edit the the following entries 
1. 'locale: "en-GB"'
2. 'title: "~/"'
3. 'name: "Thomas Naake"'
4. 'description: "Thomas Naake's GitHub pages site"'
5. 'bio: "Plants, evolution, specialized metabolism, metabolomics, transciptomics, other omics, computational biology, reproducible research, open science"


## Build locally

1. install ruby2.5-dev
2. 
3. 
sudo bundle install
bundle install
bundle exec jekyll serve

