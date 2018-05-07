---

layout: post
title: "How To: Find the size of a directory"
---

Sometimes it's very useful to know how much content is in a directory without opening a GUI interface.

In Bash:

```bash
du -cks \* | sort -n | awk '\\''BEGIN { split("KB,MB,GB,TB", Units, ","); } { u = 1;while ($1 \>= 1024){$1 = $1 / 1024;u += 1;}$1 = sprintf("%.1f %s", $1, Units\[u\]);print $0;}'\\'' | tail –11
```

I would suggest adding this to your bash aliases as `ducks`.

Output looks something like so:

    <code>
    ~ > ducks

    4.0 KB p
    72.0 KB Music
    24.1 MB Sites
    35.0 MB Downloads
    433.3 MB Dropbox
    937.5 MB Movies
    3.5 GB Library
    6.3 GB Desktop
    11.7 GB Documents
    16.5 GB Pictures
    39.5 GB total

    ~ > _
    </code>

**Update:** My good friend [Clayton](http://www.twitter.com/file_cabinet) suggested a much simpler way. The only problem is that the output is not sorted.

```bash
du -h -d 1
```

The output is the whole directory. I truncated the output to show the last 11.

    <code>
    ~ > du -h -d 1 | tail -11

    6.3G    ./Desktop
    12G     ./Documents
    212M    ./Downloads
    433M    ./Dropbox
    3.6G    ./Library
    8.0K    ./Movies
    72K     ./Music
    17G     ./Pictures
    0B      ./Public
    24M     ./Sites
    40G     .

    ~ >_
    </code>

**Update \#2:** Some systems do not accept the `-d` flag. This can be replaced with the `--max-depth` flag, like so:

```bash
du -h —max-depth 1
```
