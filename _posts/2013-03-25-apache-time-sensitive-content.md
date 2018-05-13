---
layout: post
title: "Apache time sensitive conditions"
date: 2013-03-25
---

If you'd like to do time sensitive conditionals on Apache, the following will help you get started. This is useful if you'd like certain content to be displayed based on time.

```apache
<!--#config timefmt="%Y%m%d%H%M" -->
<!--#if expr="$DATE_LOCAL < 201303281140" -->
    <!--#include virtual="before.html"-->
<!--#elif expr="$DATE_LOCAL >= 201303281140 && $DATE_LOCAL <= 201303281205"-->
    <!--#include virtual="during.html"-->
<!--#else-->
    <!--#include virtual="after.html"-->
<!--#endif-->
```

What we do here is set the time format to `%Y%m%d%H%M` which is year, month, day, hour, minute. For example "201303281140" for March 28th, 2013 at 11:40am.

Then if the current server time is before set time, we display `before.html`; if the time is during our two times, we display `during.html`; else we display `after.html`.
