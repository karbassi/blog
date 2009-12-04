--- 
layout: post
title: "How To: Find the size of a directory"
---
Sometimes it's very useful to know how much content is in a directory without opening a GUI interface.

In Bash:

{% highlight %}
du -cks * | sort -n | awk '\''BEGIN { split("KB,MB,GB,TB", Units, ","); } { u = 1;while ($1 >= 1024){$1 = $1 / 1024;u += 1;}$1 = sprintf("%.1f %s", $1, Units[u]);print $0;}'\'' | tail -11
{% endhighlight %}

I would suggest adding this to your bash aliases as <code>ducks</code>.

Output looks something like so:

    ~ > ducks
    
    4.0 KB p
    72.0 KB Music
    24.1 MB Sites
    35.0 MB Downloads
    433.3 MB Dropbox
    937.5 MB Movies
    3.5 GB Library
    6.3 GB Desktop
    11.7 GB Documents
    16.5 GB Pictures
    39.5 GB total
    
    ~ > _

**Update:** My good friend [Clayton](http://www.twitter.com/file_cabinet) suggested a much simpler way. The only problem is that the output is not sorted.

{% highlight bash %}
du -h -d 1
{% endhighlight %}

The output is the whole directory. I truncated the output to show the last 11.

    ~ > du -h -d 1 | tail -11
    
    6.3G    ./Desktop
    12G     ./Documents
    212M    ./Downloads
    433M    ./Dropbox
    3.6G    ./Library
    8.0K    ./Movies
    72K     ./Music
    17G     ./Pictures
    0B      ./Public
    24M     ./Sites
    40G     .
    
    ~ >_

**Update #2:** Some systems do not accept the <code>-d</code> flag. This can be replaced with the <code>--max-depth</code> flag, like so:

{% highlight bash %}
du -h --max-depth 1
{% endhighlight %}
