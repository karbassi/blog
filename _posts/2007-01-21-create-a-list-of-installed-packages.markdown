---
layout: post
title: Create a list of installed packages
---

Ever wanted to know what applications are actually installed on your system? Sure you can view the applications via the applications bar, but there are so many other applications not shown there.

Also, what if you have your system with all the applications you want and want to install them again on another pc (or after a reinstall)? [Cynical](http://ubuntuforums.org/showthread.php?t=261366) shows us how to do that with a few simple steps.

To output this information to a file in your home directory you would use:

{% highlight bash %}
dpkg --get-selections > installed-software
{% endhighlight %}

**Note:** <tt>installed-software</tt> is actually just a text file. You can open it to view it, but don't modify it if you don't know what you're doing. It might screw up the next step.

If you wanted to use the list to reinstall this software on a fresh Ubuntu setup or on another computer, just do the following steps:

{% highlight bash %}
dpkg --set-selections < installed-software
dselect
sudo apt-get autoremove
sudo apt-get autoclean
{% endhighlight %}
