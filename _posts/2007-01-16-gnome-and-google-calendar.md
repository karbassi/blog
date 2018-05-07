---

layout: post
title: "Gnome and Google Calendar"
---

Britt Selvitelle writes on how to combine [Google Calendar and Ubuntu](http://lukewarmtapioca.com/2006/12/8/google-calendar-meet-ubuntu). His post is based on [Bryan Clark's](http://www.gnome.org/~clarkbw/) post on [Mashing Google Calendar and GNOME](http://www.gnome.org/~clarkbw/blog/Mashing_Google_Calendar_and_GNOME).

Let's get down to business.

First open up a `terminal` by going to Applications `>` Accessories `>` Terminal (in Ubuntu) or press `Alt + F2` and type in `terminal`. Now that you have a terminal open, let's get down to viewing your history.

Ubuntu users type:

```bash
/usr/lib/evolution-webcal/evolution-webcal $GOOGLE\_ICAL\_URL
```

For any other [GNOME](http://www.gnome.org/) environment:

```bash
/usr/libexec/evolution-webcal $GOOGLE\_ICAL\_URL
```

I hope you notice the difference.