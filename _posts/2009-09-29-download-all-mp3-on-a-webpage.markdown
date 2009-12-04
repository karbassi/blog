--- 
layout: post
title: Download all mp3 on a webpage
---

Ever wanted to download all the audio files off a particular webpage? You could manually click and save each one or load up terminal and use this one-liner. **Remember** to only use this for sites that are allowing you do download their content free of charge; stealing is wrong!

{% highlight bash %}
curl -s SITEURL | \
grep -oie "\(http\|https\|ftp\|www\).*\.\(mp3\|aac\|wav\|m4a\|ogg\|flac\|aiff\|mp4\|wma\|ram\|ra\)" | \
sort | uniq | awk '{print "curl -sOL "$1" &"}' | /bin/sh
{% endhighlight %}

A quick explanation of what is happening.

{% highlight bash %}
curl -s SITEURL
{% endhighlight %}

This is downloading the SITEURL (which you should replace with the url of the site/file you want to scrape) but not outputting it nor showing the download progress. This is because of the <code>-s</code> flag that is thrown.

{% highlight bash %}
| grep -oie "\(http\|https\|ftp\|www\).*\.\(mp3\|aac\|wav\|m4a\|ogg\|flac\|aiff\|mp4\|wma\|ram\|ra\)"
{% endhighlight %}

This is parsing/scraping the site/file that we just downloaded for urls that match our regular expression. What we are looking for is urls that start with <code>http</code>, <code>https</code>, <code>ftp</code>, or <code>www</code> and that end with <code>mp3</code>, <code>aac</code>, <code>wav</code>, <code>m4a</code>, <code>ogg</code>, <code>flac</code>, <code>aiff</code>, <code>mp4</code>, <code>wma</code>, <code>ram</code>, or <code>ra</code>.

{% highlight bash %}
| sort | uniq
{% endhighlight %}

Sorts, and only displays the unique urls. No need for duplicates!

{% highlight bash %}
| awk '{print "curl -sOL "$1" &"}'
{% endhighlight %}

Displays the urls as an output of <code>curl -sOL MP3URL &</code>, which will actually download the file in the background. The <code>-O</code> flag will create a file and the <code>-L</code> flag will follow any url redirection.

{% highlight bash %}
| /bin/sh
{% endhighlight %}

Finally, the whole process is ran through the bash (shell) command.

You shouldn't see any output because everything is ran in the background. Just wait for the files to be created in the directory you are in.
