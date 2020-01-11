---
layout: post
title:  "Creating a .github.io Website"
date:   2019-12-28 17:38:00 -0500
tags: blog jekyll 
---
In this post I will describe how I made this github website. I will update this post as I add more features to the site. 

**Setting up**
1. Create a public github repository. Let the repo name be websitename.github.io (choose the website name now). 
2. Visit websitename.github.io. in order to view the live website. You should see a blank template. 
3. Set up jekyll on your local machine. Follow the setup steps listed on this tutorial: [Building a static website with Jekyll and Github][programming-historian]. I had to make two slight modifications to the steps as described below:

	* MacOS has ruby pre-installed. The command `brew install ruby` will install the newest version of ruby on your local machine. However, you have to alert your machine to look in this new directory, instead of using the default version. To do so, add the appropriate lines (displayed upon installation) to your `~/.bash_profile` file. Once this is done, `gem install rubygems-update` will work as expected. 

	* If you are running Movaje on MacOS, you first need to `sudo installer -pkg /Library/Developer/CommandLineTools/Packages/macOS_SDK_headers_for_macOS_10.14.pkg -target /` before running `gem install jekyll`.

**File Layout**
<div class="row">
  <div class="column">
	<img src="/assets/layout.png">
  </div>
  <div class="column" markdown="1">
	Have **fun**
  </div>
</div>


**Overriding Defaults**

**Adding Tags**

Fix footer size

1/9/20
Added images (profile picture and meme)
Jank CSS

1/10/20
Created food template

TODO:
- Optimize image load times
- Make website mobile friendly
- Add pageinator for blog posts

[programming-historian]: https://programminghistorian.org/en/lessons/building-static-sites-with-jekyll-github-pages
