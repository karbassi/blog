---
layout: post
title: "How To: Remove Duplicate Lines From A File"
date: 2009-05-28
---

Sure you can load up a bulky editor and use its tools to do that, but why not do it in much faster in bash with `awk`.

In Bash:

```bash
awk '!x[$0]++' in.txt > out.txt
```

Wasn't that easy?
