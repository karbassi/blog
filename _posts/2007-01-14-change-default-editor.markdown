---
layout: post
title: Change default editor
---

There is a quick way to change your default editor, whichever you want.

First open up a <tt>terminal</tt> by going to <tt>Applications > Accessories > Terminal</tt> (in Ubuntu) or press <tt>Alt + F2</tt> and type in <tt>terminal</tt>. Now that you have a terminal open, let's get down to viewing your history.

Open up <tt>.bashrc</tt> by typing:

{% highlight bash %}
gedit ~/.bashrc
{% endhighlight %}

Now to change your bash default editor find

{% highlight bash %}
export EDITOR
{% endhighlight %}

However, if you can't find that, just add this to the top.

{% highlight bash %}
export EDITOR=gedit
{% endhighlight %}

Personally I like <tt>gedit</tt>. You can use <tt>pico</tt> (<tt>/usr/bin/pico</tt>), <tt>nano</tt> (<tt>/usr/bin/nano</tt>), or any other editor you like.

Like always, you can learn more about this by doing the following:

{% highlight bash %}
man bash
{% endhighlight %}
