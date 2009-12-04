---
layout: post
title: Cols and Colgroups
---

Who loves working with tables in <abbr title="Hypertext Markup Language">HTML</abbr> or <abbr title="Extensible HyperText Markup Language">XHTML</abbr>? **&lt;sarcasm&gt; I know I do! &lt;/sarcasm&gt;** Recently I've been working with trying to get a column in a table to format correctly. It's something very simple; I have 3 columns and X rows. I want the first column to be aligned left while the other columns to aligned right. Also, I want to style each column differently. Going through <acronym title="World Wide Web Consortium">[W3C][1]</acronym>'s [HTML 4.01 Specification][2], I found [column groups][3]. After a few minutes of reading, it looked like exactly what I needed.


I grabbed [W3C's sample table][4] to test with. Wow, that didn't work. I dumped their code into a page (and fixed it so it validates with XHTML 1.0 Strict) so you can see it's not what they say it should be. Surprisingly it doesn't work the way they say it does.


I went looking for some answers and [Mark J. Reed][5] said it best:

>First, you should know that due to the CSS rendering model, &lt;col> and &lt;colgroup> are both severely limited in what styling they support (at least outside of IE, which violates the CSS rendering model to provide them more power, breaking other things in the process). To be precise, there are only four things you're allowed to do with a table-column (individual or group) style:
>
>   - set the background color
>   - set the width
>   - set up a border
>   - control visibility
>
>That's it. You can't make a column bold or in a different font or give it centered text or any of the other things that seem perfectly reasonable before you dive into the detailed requirements of the CSS spec.

So what now? Will HTML5 fix this? I rather not use some hack to do something that should work already.

[1]: http://www.w3.org
[2]: http://www.w3.org/TR/html4 "HTML 4.01 Specification"
[3]: http://www.w3.org/TR/html4/struct/tables.html#h-11.2.4 "Column groups: the COLGROUP and COL elements"
[4]: http://www.w3.org/TR/html4/struct/tables.html#sample
[5]: http://archivist.incutio.com/viewlist/css-discuss/79793 (Styling tables with <code>&lt;colgroup&gt;</code> & &lt;col&gt;)
