---
layout: posts
title: "Update all Ruby gems"
categories:
  - Ruby
tags:
  - link
  - Post Formats
---

Last week i wanted to update some ruby projects that i have packed in gems and wanted to update their dependencies (just to have the project updated).
My objective was to be able to update all my gems in a single bash line, luckily i managed to do this by issuing the following line:

{% highlight bash %}

sudo gem update `gem list | cut -d ' ' -f 1`

{% endhighlight %}
