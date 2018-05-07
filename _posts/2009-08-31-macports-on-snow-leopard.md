---

layout: post
title: "MacPorts on Snow Leopard"
---

> **Update: 2010** I would highly suggest moving away from MacPorts/Fink and to use [Homebrew](http://mxcl.github.com/homebrew/) by [Max Howell](http://methylblue.com/).
> **Update:** The nice people at MacPorts have update the package to v1.8.0. You can follow [their instructions](http://trac.macports.org/post/macports-180-now-available/) to upgrade to the latest stable version. I would suggest the [MacPorts v1.8.0 for OS X 10.6 DMG](http://distfiles.macports.org/MacPorts/MacPorts-1.8.0-10.6-SnowLeopard.dmg) file.

After installing Snow Leopard, you may want to install the MacPorts. Follow the following steps to get it up and running:

1\. Download and install [XCode](http://developer.apple.com/mac/) from ADC.
2\. Open up the Terminal
3\. `svn co http://svn.macports.org/repository/macports/trunk/base/`
4\. `cd base`
5\. `./configure`
6\. `make`
7\. `sudo make install`
8\. `sudo /opt/local/bin/port -v selfupdate`
9\. `sudo port upgrade --enforce-variants` (Did not work for me)
10\. `sudo port upgrade outdated` (Did not work for me)