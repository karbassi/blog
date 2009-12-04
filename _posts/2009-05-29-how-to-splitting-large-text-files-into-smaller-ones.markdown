--- 
layout: post
title: "How To: Splitting large text files into smaller ones"
---
Let's say you have a **huge** text file with couple million lines. Now you want to split it up into 100, 200, or 300 line files. Bash makes it pretty easy with <code>split</code>.

In Bash:

{% highlight bash %}
split -l 500 file.txt
{% endhighlight %}

That splits up the file <code>file.txt</code> into 500 line chunks. What is produced are files such as <code>xaa</code>, <code>xab</code>, <code>xac</code> and so on.

Be sure to do <code>man split</code> for more options.
