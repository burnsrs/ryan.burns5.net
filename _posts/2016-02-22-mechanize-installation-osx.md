---
layout: post
title:  "Mechanize rubygem installation on OS X"
date:   2016-02-22 20:00:00 -0500
categories: blog ruby osx
summary: Solving installation problems for mechanize on OS X.
---

I was needing to test some screen scraping and wanted to use ruby and mechanize gem to do so.  Trying to install mechanize on OS X El Capitan was failing when trying to build one of its dependencies, nokogiri. It was failing due to do not being able to find libxml2 ("libxml2 is missing").  Installing nokogiri as show below works and then allows mechanize to be installed.

{% highlight shell %}
sudo gem install nokogiri -- --with-xml2-include=/Applications/Xcode.app/Contents/Developer/Platforms/MacOSX.platform/Developer/SDKs/MacOSX10.11.sdk/usr/include/libxml2 --use-system-libraries
{% endhighlight %}
