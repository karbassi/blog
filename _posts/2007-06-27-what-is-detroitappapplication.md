---
layout: post
title: "What is detroit.app.Application?"
date: 2007-06-27
---

Recently [Google Docs & Spreadsheets] released a [new version] of their wonderful application. It's a wonderful new interface and foreshadows what Google Docs is going to turn into.

Like always, I went snooping around to see what I could find. It's usually fun to see what they didn't implement yet. Taking a look at the [javascript source] (notice the link might change) I found something very interesting.

```javascript
ac[_P].Ca = function()
{
   throw Error("[detroit.app.Application] Not implemented");
};
```

Apart from it being "Google Code" (no useful variable names), it shows that their is an application called "detroit.app" being developed. There is a [Google Sales office in Detroit], but apart from that, I could not find anything related.

Most applications will have a codename before it's final release. So now our part is to figure out what "detroit.app.Application" is.

> **Update:** There seems to be many calls to "detroit.ui." however. One of them is "detroit.ui.Pager". The name "detroit" could be the code-name for the next release.

[Google Docs & Spreadsheets]: http://docs.google.com
[new version]: http://google-d-s.blogspot.com/2007/06/entirely-new-way-to-stay-organized.html
[javascript source]: http://docs.google.com/doclist/client/js/434292853-doclist_local.js
[Google Sales office in Detroit]: http://maps.google.com/maps?q=2000+Town+Center,+Suite+1900,+Southfield,+MI+(Google+Detroit)
