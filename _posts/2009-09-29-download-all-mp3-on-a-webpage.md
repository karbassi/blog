---
layout: post
title: "Download all mp3 on a webpage"
date: 2009-09-29
---

> **Update:** Be sure to escape any urls are are using. Characters like `(`, `)`, and others need to be escaped. This can be done by putting a backslash before them. For example: `\(` `\)`

Ever wanted to download all the audio files off a particular webpage? You could manually click and save each one or load up terminal and use this one-liner. **Remember** to only use this for sites that are allowing you do download their content free of charge; stealing is wrong!

```bash
curl -s SITEURL | grep -oie "\(http\|https\|ftp\|www\).*\.\(mp3\|wav\|m4a\|ogg\|mp4\)" | sort | uniq | awk '{print "curl -sOL "$1" &"}' | /bin/sh
```

A quick explanation of what is happening.

```bash
curl -s SITEURL
```

This is downloading the SITEURL (which you should replace with the url of the site/file you want to scrape) but not outputting it nor showing the download progress. This is because of the `-s` flag that is thrown.

```bash
grep -oie "\(http\|https\|ftp\|www\).*\.\(mp3\|wav\|m4a\|ogg\|mp4\)"
```

This is parsing/scraping the site/file that we just downloaded for urls that match our regular expression. What we are looking for is urls that start with `http`, `https`, `ftp`, or `www` and that end with `mp3`,  `wav`, `m4a`, `ogg`, or `mp4`. You can add your own file extensions; just follow the pattern.

```bash
sort | uniq
```

Sorts, and only displays the unique urls. No need for duplicates!

```bash
awk '{print "curl -sOL "$1" &"}'
```

Displays the urls as an output of `curl -sOL MP3URL &`, which will actually download the file in the background. The `-O` flag will create a file and the `-L` flag will follow any url redirection.

```bash
/bin/sh
```

Finally, the whole process is ran through the bash (shell) command.

You shouldn't see any output because everything is ran in the background. Just wait for the files to be created in the directory you are in.
