---
title: "lala extremely flawed"
date: 2009-12-12
---

A week ago I wrote about how I used [web apps to feed into other web apps], more specifically I talked about [lala] and it's "[lala music mover]".

Recently a thought formed; while watching how lala's music mover worked, I noticed that it wasn't checking anything _other_ than the [ID3] tag. I ran a real quick experiment.

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
[id3]: http://en.wikipedia.org/wiki/ID3
[fireflies]: http://lala.com/zyhS
[lala-fireflies]: 1-lala-fireflies.png
[lala-fireflies-none]: 2-lala-fireflies-none.png
[itunes-sample-mp3]: 3-itunes-sample-mp3.png
[id3-sample]: 4-ID3-sample.png
[id3-firefly]: 5-ID3-firefly.png
[itunes-firefly]: 6-itunes-firefly.png
[lal-mover]: 7-lal-mover.png
[lala-fireflies-have]: 8-lala-fireflies-have.png
