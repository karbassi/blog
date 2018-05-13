---
layout: post
title: "MacPorts on Snow Leopard"
date: 2009-08-31
---

> **Update in 2010:** I would highly suggest moving away from MacPorts/Fink and to use [Homebrew] by [Max Howell].
>
> **Update:** The nice people at MacPorts have update the package to v1.8.0. You can follow [their instructions] to upgrade to the latest stable version. I would suggest the [MacPorts v1.8.0 for OS X 10.6 DMG] file.

After installing Snow Leopard, you may want to install the MacPorts.
Follow the following steps to get it up and running:

1. Download and install [XCode] from ADC.
2. Open up the Terminal
3. `svn co http://svn.macports.org/repository/macports/trunk/base/`
4. `cd base`
5. `./configure`
6. `make`
7. `sudo make install`
8. `sudo /opt/local/bin/port -v selfupdate`
9. `sudo port upgrade --enforce-variants` (Did not work for me)
10. `sudo port upgrade outdated` (Did not work for me)

[Homebrew]: http://mxcl.github.com/homebrew/
[Max Howell]: http://methylblue.com/
[their instructions]: http://trac.macports.org/post/macports-180-now-available/
[MacPorts v1.8.0 for OS X 10.6 DMG]: http://distfiles.macports.org/MacPorts/MacPorts-1.8.0-10.6-SnowLeopard.dmg
[XCode]: http://developer.apple.com/mac/
