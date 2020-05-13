---
title: "Gnome and Google Calendar"
date: 2007-01-16
---

Britt Selvitelle writes on how to combine [Google Calendar and Ubuntu]. His post is based on [Bryan Clark's] post on [Mashing Google Calendar and GNOME][1].

Let's get down to business.

First open up a `terminal` by going to **Applications > Accessories > Terminal** (in Ubuntu) or press `Alt + F2` and type in `terminal`. Now that you have a terminal open, let's get down to viewing your history.

Ubuntu users type:

```bash
/usr/lib/evolution-webcal/evolution-webcal $GOOGLE_ICAL_URL
```

For any other [GNOME][2] environment:

```bash
/usr/libexec/evolution-webcal $GOOGLE_ICAL_URL
```

I hope you notice the difference.

[google calendar and ubuntu]: http://lukewarmtapioca.com/2006/12/8/google-calendar-meet-ubuntu
[bryan clark's]: http://www.gnome.org/~clarkbw/
[1]: http://www.gnome.org/~clarkbw/blog/Mashing_Google_Calendar_and_GNOME
[2]: http://www.gnome.org/
