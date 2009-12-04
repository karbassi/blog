--- 
layout: post
title: "How To: Remove Duplicate Lines From A File"
---
Sure you can load up a bulky editor and use its tools to do that, but why not do it in much faster in bash with <code>awk</code>.

In Bash:

{% highlight bash%}
awk '!x[$0]++' in.txt > out.txt
{% endhighlight %}

Wasn't that easy?
