---
layout: post
title: "Copy (cp) with progress bar"
date: 2013-04-10
---

Many times you'd like to see the progress of a copy but sadly `cp` doesn't have that feature.

Many posts online will show bash scripts that pipe `cp` into `grep`/`awk`/etc or use tools like `pv`. Alas, there is a much more simple way. Use `rsync`.

```bash
rsync -a --progress SOURCE_FOLDER DESTINATION_FOLDER
```

Throw the `--stats` flag for some stats after the transfer is done.

```bash
rsync -a --stats --progress SOURCE_FOLDER DESTINATION_FOLDER
```
