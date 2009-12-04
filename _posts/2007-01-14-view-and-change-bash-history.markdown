--- 
layout: post
title: View and Change bash history
---

Always wanted to know what you have been doing via bash? Did you know bash keeps a history of that? Here is a quick way to check it and an easy way to change the history limit.

First open up a <tt>terminal</tt> by going to <tt>Applications > Accessories > Terminal</tt> (in Ubuntu) or press <tt>Alt + F2</tt> and type in <tt>terminal</tt>. Now that you have a terminal open, let's get down to viewing your history.

To view your history via the terminal, type:

{% highlight bash %}
history
{% endhighlight %}

This will show the whole list.

To view your history in a editor (to save for later), just type:

{% highlight bash %}
history -w ~/history.txt
gedit ~/history.txt
{% endhighlight %}

What <tt>history -w ~/history.txt</tt> does is save the <tt>history</tt> to a file named <tt>history.txt</tt> on your home folder (<tt>cd ~/</tt>). The next command opens up the file for viewing in <tt>gedit</tt>.</p>

**Note:** For more information about <tt>history</tt> be sure to use the man pages by doing:

{% highlight bash %}
man history
{% endhighlight %}

Now to change your bash history length, just open up your <tt>.bashrc</tt> by doing so:

{% highlight bash %}
gedit ~/.bashrc
{% endhighlight %}

Once open, at the top add

{% highlight bash %}
export HISTFILESIZE=3000
{% endhighlight %}

As you can see, the limit can be changed.

Bash keeps it's own history in a file. You can view that file as stated before, or by opening <tt>~./bash_history</tt>