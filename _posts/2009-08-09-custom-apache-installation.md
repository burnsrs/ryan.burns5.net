---
layout: post
title:  "Custom Apache Installation"
date:   2009-08-09 12:00:00 -0500
categories: blog apache osx
summary: I wanted to document my process for installing/upgrading to the latest version of Apache on a Mac OS X machine.
---
I wanted to document my process for installing/upgrading to the latest version of Apache on a Mac OS X machine.  The steps below will guide you through the process. Lets get the latest bits from apache.org.  We want to get the Unix source files, I usually get the .tar.gz file.  The downloads are accessible [here](http://httpd.apache.org/download.cgi) Now, unpack the bits and open a terminal window and change directory to the location of the unpacked files.  We will begin by configuring our install.  I've included various options that I need, but you can find out what options are available [here](http://httpd.apache.org/docs/2.2/programs/configure.html).

{% highlight shell %}
CFLAGS="-arch i386 -isysroot /Developer/SDKs/MacOSX10.5.sdk" \  
./configure --prefix=/Developer/Servers/apache_2.2.13 \  
--enable-mods-shared=all \  
--enable-cache \  
--enable-disk-cache \  
--enable-deflate \  
--enable-expires \  
--enable-headers \  
--enable-info \  
--enable-mime-magic \  
--enable-proxy \  
--enable-rewrite \  
--enable-speling \  
--enable-unique-id \  
--enable-usertrack
{% endhighlight %}

Now lets make the install.

{% highlight shell %}
make
{% endhighlight %}

Now lets install.

{% highlight shell %}
make install
{% endhighlight %}

Now we can start the server.

{% highlight shell %}
sudo /Developer/Servers/apache_2.2.13/bin/./apachectl restart
{% endhighlight %}

All done.
