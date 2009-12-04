--- 
wordpress_id: 113885804
layout: post
title: Find & Replace in Linux/Mac
wordpress_url: http://my.tumblr.com/post/113885804
---
This is a quick one liner to find and replace strings in *nix. You can use this in your Mac terminal or Unix prompt.

In Bash:

{% highlight bash %}
find ./ -type f -exec sed -i 's/FIND/REPLACE/g' {} \;
{% endhighlight %}

Example:

{% highlight bash %}
find ./ -type f -exec sed -i 's/signin/login/g' {} \;
{% endhighlight %}
