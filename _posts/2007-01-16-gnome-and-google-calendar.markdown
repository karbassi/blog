---
layout: post
title: Gnome and Google Calendar
---

Britt Selvitelle writes on how to combine [Google Calendar and Ubuntu][1]. His post is based on [Bryan Clark][2]'s post on [Mashing Google Calendar and GNOME][3].

Let's get down to business.

First open up a <tt>terminal</tt> by going to <tt>Applications > Accessories > Terminal</tt> (in Ubuntu) or press <tt>Alt + F2</tt> and type in <tt>terminal</tt>. Now that you have a terminal open, let's get down to viewing your history.

Ubuntu users type:
{% highlight bash %}
/usr/lib/evolution-webcal/evolution-webcal $GOOGLE_ICAL_URL
{% endhighlight %}

For any other "GNOME":http://www.gnome.org/ environment:
{% highlight bash %}
/usr/libexec/evolution-webcal $GOOGLE_ICAL_URL
{% endhighlight %}

I hope you notice the difference.

[1]: http://lukewarmtapioca.com/2006/12/8/google-calendar-meet-ubuntu
[2]: http://www.gnome.org/~clarkbw/
[3]: http://www.gnome.org/~clarkbw/blog/Mashing_Google_Calendar_and_GNOME