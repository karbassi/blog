---

layout: post
title: "How To: Splitting large text files into smaller ones"
---

Let's say you have a **huge** text file with couple million lines. Now you want to split it up into 100, 200, or 300 line files. Bash makes it pretty easy with `split`.

In Bash:

```bash
split -l 500 file.txt
```

That splits up the file `file.txt` into 500 line chunks. What is produced are files such as `xaa`, `xab`, `xac` and so on.

Be sure to do `man split` for more options.
