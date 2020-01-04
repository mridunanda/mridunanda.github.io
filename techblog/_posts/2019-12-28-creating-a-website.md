---
layout: post
title:  "Creating a .github.io Website"
date:   2019-12-28 17:38:00 -0500
tags: blog
---
12/28/2019:
In this post I will describe how I made this github website. I will update this post as I add more features to the site. 
I started by creating a github repository (make it public and let the repo name be websitename.github.io).
You can see your website live right after creaing the repo (just visit the url that you just created in the repo name).
The next step is to set up jekyll on your local machine. To do so, I followed this tutorial: [Building a static website with Jekyll and Github][programming-historian]

Two things to note in the insallation steps from the above tutorial:
1. MacOS has ruby pre-installed. The command `brew install ruby` will install the newest version of ruby on your local machine. However, you have to alert your machine to look in this new directory, instead of using the default version. To do so, add the appropriate lines (displayed upon installation) to your `~/.bash_profile` file. Once this is done, `gem install rubygems-update` will work as expected. 
2. If you are running Movaje on MacOS, you first need to `sudo installer -pkg /Library/Developer/CommandLineTools/Packages/macOS_SDK_headers_for_macOS_10.14.pkg -target /` before running `gem install jekyll`.

Jekyll requires blog post files to be named according to the following format:

`YEAR-MONTH-DAY-title.MARKUP`

Where `YEAR` is a four-digit number, `MONTH` and `DAY` are both two-digit numbers, and `MARKUP` is the file extension representing the format used in the file. After that, include the necessary front matter. Take a look at the source for this post to get an idea about how it works.

Jekyll also offers powerful support for code snippets:

{% highlight ruby %}
def print_hi(name)
  puts "Hi, #{name}"
end
print_hi('Tom')
#=> prints 'Hi, Tom' to STDOUT.
{% endhighlight %}

Check out the [Jekyll docs][jekyll-docs] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll’s GitHub repo][jekyll-gh]. If you have questions, you can ask them on [Jekyll Talk][jekyll-talk].

[programming-historian]: https://programminghistorian.org/en/lessons/building-static-sites-with-jekyll-github-pages
[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
