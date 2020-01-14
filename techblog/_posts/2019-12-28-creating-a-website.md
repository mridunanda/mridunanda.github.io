---
layout: post
title:  "Creating a .github.io Website"
date:   2019-12-28 17:38:00 -0500
tags: blog jekyll 
---
In this post I will describe how I made this github website. I will update this post as I add more features to the site. 

**Setting up**
1. Create a public github repository. Let the repo name be ***websitename**.github.io* (choose the website name now). 
2. Visit ***websitename**.github.io*. in order to view the live website. You should see a blank template. 
3. Set up jekyll on your local machine. Follow the setup steps listed on this tutorial: [Building a static website with Jekyll and Github][programming-historian]. I had to make two slight modifications to the steps as described below:

	* MacOS has ruby pre-installed. The command `brew install ruby` will install the newest version of ruby on your local machine. However, you have to alert your machine to look in this new directory, instead of using the default version. To do so, add the appropriate lines (displayed upon installation) to your *~/.bash_profile*. Once this is done, `gem install rubygems-update` will work as expected. 

	* If you are running Movaje on MacOS, you first need to:
	<br>
	`sudo installer -pkg /Library/Developer/CommandLineTools/Packages/macOS_SDK_headers_for_macOS_10.14.pkg -target /` 
	<br>
	before running `gem install jekyll`.

**File Layout**
<div class="row">
  <div class="column">
	<img src="/assets/layout.png" style="width:100%" >
  </div>
  <div class="column">
	<ul> 
	  <li> <i>_config.yml</i>: This file lists the overall configuration for the website. For example, this might include a built in theme for the website, the website's title, and social media links. </li>
	  <li> <i>_drafts </i>: This folder contains posts that are not ready yet to be published. </li>
	  <li> <i>_includes </i>: This and the following folder contains the html templates for the website. This folder contains templates that will be used for multiple pages and should be kept consistent(ie the header and footer) </li>
	  <li> <i>_layouts </i>: This folder also contains html templates. However, these templates are page specific (ie a template for the food blog). </li>
	  <li> <i> _posts </i> This folder contains all the posts for the blog. Posts should be labeled by year-month-day-title (or as specified in the <i>_config.yml</i> file). In the case that you want a multi-blog website, create folders blog1 and blog2, each with their own <i>_/posts</i> folder. Then update the _posts folder accordingly. For more information for creating a multi-blog website look at the third asnwer in this post: <a href="https://stackoverflow.com/questions/14560687/multiple-blogs-in-single-jekyll-website">Multiple blogs in Jekyll Website</a></li>
	  <li> <i> _sass </i> This folder will contain all the CSS style sheets for the html pages. </li>
	  <li> <i> assets </i> (not shown in picture): place all images and js in this folder. </li>
	  <li> <i> _site </i>: This folder will contain the html created by Jekyll. No need to touch this folder. </li>
	  <li> <i> index.md </i>: This file located in the home folder will be the homepage for hte website. For other landing pages, (ex. food blog page) create a new folder (<i>/foodblog</i>) and create the index.md page inside (along with the <i>/_posts</i> folder if applicable). </li>
	  <li> <i> _data </i> (not showin in picture): This folder is useful for containing entries that have similar fields repeated multiple times. For example, I stored my projects and recipes information in this folder. </li>
	</ul>
  </div>
</div>


**Overriding Defaults**

This site is based on the jekyll theme minima. This is configured in the *_config.yml* file. As a result, alot of the above described folders will not be automatically visible after first creating the website. 

In order to customize the minima (or any other theme), do the following:
1. First locate where the theme stores the files by running `open $(bundle show minima)` replacing  minima with your theme name. 
`
2. Locate the file you want to customize and copy the file along with directory structure. For example, if you want to customize the foooter, then copy *_includes\footer.html* on your local machine.


[Customizing Jekyll Themes][jekyll-manual] is a helpful link to look at.


**Adding Tags**

Jekyll doesn't offer built in support for tags. However this website provides a great step by step explanation on how to add tags to your posts: [Jekyll Tags on Github Pages][long-qian].


**Customizing Header**

The default setting in the Jekyll Minima theme is to autoinclude all pages with a front-matter title in the header. However, I wanted to modify this so that only a select few pages would show up. To do so I followed the isntructions listed on this post: [Customizing Minima Header][github-jekyll]. I have copied the solution below for completeness.

1. Add `hide_header_link: true` to the front matter of all websites that should not be displayed on the header. For example, I added this to the front-matter of my tagpages.
2. Add the following code to *_includes/header.html*:{% raw %}
<br>
`{% for my_page in site.pages %}`
<br> &nbsp; &nbsp;
    `{% if my_page.hide_header_link %}{% continue %}{% endif %}`
{% endraw %}


**Some Jank CSS**

Alas, the time had come to start customizing the looks of my website... "NOOOOOOO!!" I wailed. It is time to learn CSS. The basic steps to modifying any element of the webpage are:

1. Copy the *_sass* folder to your local machine.
2. Modify an existing .attribute, or add a new one in either the *_base.scss* or *_layout.scss* files.
3. Refer to this new attribute in the html templates. For example `<div class="new-thing-i-defined"> ...` 

I modified several parts of the original minima theme using the above steps. For example:
- [Modify Jekyll Header Size][stackoverflow-header]
- [Gallery Template][mattvh-theme] used for food blog 
- [Two Column Layout][w3-school] on this page (above)
- [Left Aligning][interneting-is-hard] my profile picture on the homepage (inside the wrapper). 
	- I used a hack method in order to [Remove Extra Space from the top of a CSS column][stackoverflow-css]
- [Creating Photo Gallery][w3-gallery] for food blog

<i> A painful lesson: </i> <span style="color:red"><i> Your browser caches the CSS. Therefore if you update your CSS and view it on Github, it will still look like the old template. This might make you feel a lot crazy and a bit sad. Don't fret. Just clear your brower cookies and cache and the new CSS should be loaded. All is well again. Godspeed. </i></span>

**Liquid and _data folder**

Liquid is a handy templating language which makes life so much easier. Examples of this site making use of liquid can be found in the index.md file inside the projects folder and the foodpost.html file in the _layout folder. 

I did learn one <span style="color:red"><i>painful lesson</i></span> with Liquid however... That is the increment tag. 
You see, I, a simple person, wanted to create a nice template for future posts.
To do so, I needed to make a for loop, to enumerate pictures inside of my gallery. 
However, this is where I fell into the trap of the <span style="color:red"><i><b> evil </b></i></span> increment tag!!. 
<u>Note: the increment tag creates a new reference to the variable, initialized to 0 and then increments that value </u>.
[Read this documentation][shopify] and then [This workaround][stackoverflow-liquid].
peace and love.

**TODO**
- Clean up CSS
- Link PDFs without google docs
- Optimize image load times
- Make website mobile friendly
- Add pageinator for blog posts
- Add more theme customizations via Bootstrap

[programming-historian]: https://programminghistorian.org/en/lessons/building-static-sites-with-jekyll-github-pages
[jekyll-manual]: https://jekyllrb.com/docs/themes/
[long-qian]: https://longqian.me/2017/02/09/github-jekyll-tag/
[github-jekyll]: https://github.com/jekyll/minima/issues/19
[stackoverflow-header]:https://stackoverflow.com/questions/38705593/full-width-header-in-jekyll
[mattvh-theme]:https://github.com/mattvh/jekyllthemes/blob/master/assets/css/jekyllthemes.css
[w3-school]:https://www.w3schools.com/howto/howto_css_two_columns.asp
[interneting-is-hard]:https://internetingishard.com/html-and-css/floats/
[stackoverflow-css]:https://stackoverflow.com/questions/36392351/remove-extra-space-from-top-of-css-columns-in-chrome
[w3-gallery]:https://www.w3schools.com/howto/howto_js_slideshow_gallery.asp
[shopify]:https://shopify.github.io/liquid/tags/variable/
[stackoverflow-liquid]:https://stackoverflow.com/questions/48046411/how-to-increment-the-counter-inside-a-liquid-for-loop
