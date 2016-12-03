---
layout: post
title:  "Java Problems on Snow Leopard"
date:   2009-08-29 12:00:00 -0500
categories: blog java osx coldfusion
summary: Solution to possible problems with java on Snow Leopard.
---

**UPDATE** Need to say that I have completed a clean install of Snow Leopard and Java 1.6 seems to be working fine for my previous issues, but still think the post would be helpful in getting Java 1.5 installed if needed.

***

I heard earlier via twitter that some have had trouble with the ColdFusion 8 Installer on Apple's latest version of OS X, Snow Leopard.  I also ran into some issues with the Juniper Odyssey wireless access client which was related to this.  Below is the Java 1.5 version from Leopard for use on Snow Leopard. First grab the download [here](http://dl.getdropbox.com/u/80181/blog/java.1.5.0-leopard.tar.gz). Then, in terminal:

{% highlight shell %}
cd /tmp  
cp ~/Downloads/java.1.5.0-leopard.tar.gz .  
tar -xvzf java.1.5.0-leopard.tar.gz  
{% endhighlight %}

Now lets move the extracted 1.5.0 folder to the system Java location:

{% highlight shell %}
sudo mv 1.5.0 /System/Library/Frameworks/JavaVM.framework/Versions/1.5.0-leopard  
{% endhighlight %}

Now when Snow Leopard installed it made a symbolic link for 1.5.0 pointing to the 1.6 version, we need to clean this up:

{% highlight shell %}
cd /System/Library/Frameworks/JavaVM.framework/Versions/  
sudo mv 1.5.0 1.5.0-original  
sudo ln -s 1.5.0-leopard 1.5.0  
{% endhighlight %}

At this point you should be able to go into your Java Preferences located at /Applications/Utilities/Java Preferences and drag the J2SE 5.0 entry above the Java SE 6 entry in the Java Applications sections.

![OpenBD Admin](/images/JavaPreferences.jpg)

After arranging the order correctly the ColdFusion 8 installer should run fine.

![OpenBD Admin](/images/ColdFusion8.jpg)
