---
layout: post
title: "lala extremely flawed"
date: 2009-12-12
---

A week ago I wrote about how I used [web apps to feed into other web apps], more specifically I talked about [lala] and it's "[lala music mover]".

Recently a thought formed; while watching how lala's music mover worked, I noticed that it wasn't checking anything *other* than the [ID3] tag. I ran a real quick experiment.

To test this out, I found a song that I didn't already have. "[Fireflies]" by "Owl City" seemed a great fit. I made a clean iTunes library, created a sample mp3 and added it to iTunes. Then, I just edited the ID3 tag to match some basic information about the Fireflies track. Finally I made the lala mover rescan my library. Surprisingly when I checked lala, they had added it to my library.

What does this teach us? The lala mover does nothing but check for ID3 tags. But really, I just saved 10&cent;. It's not possible to download the track from lala being that they think I already own the track.

![lala-fireflies]
![lala-fireflies-none]
![itunes-sample-mp3]
![ID3-sample]
![ID3-firefly]
![itunes-firefly]
![lal-mover]
![lala-fireflies-have]


[web apps to feed into other web apps]: http://tech.karbassi.com/2009/12/08/web-apps-feeding-web-apps/
[lala]: http://www.lala.com
[lala music mover]: http://www.lala.com/musicmover/uploader
[ID3]: http://en.wikipedia.org/wiki/ID3
[Fireflies]: http://lala.com/zyhS
[lala-fireflies]: http://tech.karbassi.com/images/posts/2009-12-12/1-lala-fireflies.png
[lala-fireflies-none]: http://tech.karbassi.com/images/posts/2009-12-12/2-lala-fireflies-none.png
[itunes-sample-mp3]: http://tech.karbassi.com/images/posts/2009-12-12/3-itunes-sample-mp3.png
[ID3-sample]: http://tech.karbassi.com/images/posts/2009-12-12/4-ID3-sample.png
[ID3-firefly]: http://tech.karbassi.com/images/posts/2009-12-12/5-ID3-firefly.png
[itunes-firefly]: http://tech.karbassi.com/images/posts/2009-12-12/6-itunes-firefly.png
[lal-mover]: http://tech.karbassi.com/images/posts/2009-12-12/7-lal-mover.png
[lala-fireflies-have]: http://tech.karbassi.com/images/posts/2009-12-12/8-lala-fireflies-have.png
