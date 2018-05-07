---

layout: post
title: "Cols and Colgroups"
---

Who loves working with tables in HTML (Hypertext Markup Language) or XHTML (Extensible HyperText Markup Language)? **`<sarcasm>` I know I do\! `</sarcasm>`** Recently I've been working with trying to get a column in a table to format correctly. It's something very simple; I have 3 columns and X rows. I want the first column to be aligned left while the other columns to aligned right. Also, I want to style each column differently. Going through [W3C(World Wide Web Consortium)'s](http://www.w3.org) [HTML 4.01 Specification](http://www.w3.org/TR/html4), I found [column groups](http://www.w3.org/TR/html4/struct/tables.html#h-11.2.4). After a few minutes of reading, it looked like exactly what I needed.

I grabbed [W3C's sample table](http://www.w3.org/TR/html4/struct/tables.html#sample) to test with. Wow, that didn't work. I dumped their code into a page (and fixed it so it validates with XHTML 1.0 Strict) so you can see it's not what they say it should be. Surprisingly it doesn't work the way they say it does.

I went looking for some answers and [Mark J. Reed](http://archivist.incutio.com/viewlist/css-discuss/79793) said it best:

> First, you should know that due to the CSS rendering model, `<col>` and `<colgroup>` are both severely limited in what styling they support (at least outside of IE, which violates the CSS rendering model to provide them more power, breaking other things in the process). To be precise, there are only four things you're allowed to do with a table-column (individual or group) style:

  - set the background color
  - set the width
  - set up a border
  - control visibility
    That's it. You can't make a column bold or in a different font or give it centered text or any of the other things that seem perfectly reasonable before you dive into the detailed requirements of the CSS spec.

So what now? Will HTML5 fix this? I rather not use some hack to do something that should work already.
