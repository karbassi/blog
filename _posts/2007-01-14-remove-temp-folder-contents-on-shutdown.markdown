---
layout: post
title: Remove temp folder contents on shutdown
---

A few days ago Codejacked wrote an article talking about [Delete your TEMP files on shutdown](http://www.codejacked.com/delete-your-temp-files-on-shutdown/) for Windows. As much as I loved the article, I have recently switched over to [Ubuntu](http://www.ubuntu.com). Like all Operating Systems, GNU Linux has temporary files also. Here's how to delete them on shutdown.

1. Back up what you're going to working on.

    {% highlight bash %}
    sudo cp /etc/init.d/sysklogd /etc/init.d/sysklogd_backup
    {% endhighlight %}

2. Open the file in <tt>gedit</tt>

    {% highlight bash %}
    gksudo gedit /etc/init.d/sysklogd
    {% endhighlight %}

3. Find the following section

    {% highlight bash %}
    ...
    stop)
    log_begin_msg "Stopping system log daemon..."
    start-stop-daemon --stop --quiet --oknodo --exec $binpath --pidfile $pidfile
    log_end_msg $?
    ...
    {% endhighlight %}

4. Add the following line after <tt>log_end_msg $?</tt> or before <tt>;;</tt>.

    {% highlight bash %}
    rm -fr /tmp/* /tmp/.??*
    {% endhighlight %}

5. Save the file and you're set!

