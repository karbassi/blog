--- 
layout: post
title: MacPorts on Snow Leopard
---
**Update:** The nice people at MacPorts have update the package to v1.8.0. You can follow [their instructions][1] to upgrade to the latest stable version. I would suggest the [MacPorts v1.8.0 for OS X 10.6 DMG][2] file.

After installing Snow Leopard, you may want to install the MacPorts. Follow the following steps to get it up and running:

1. Download and install [XCode][3] from ADC.
2. Open up the Terminal
3. <code>svn co http://svn.macports.org/repository/macports/trunk/base/</code>
4. <code>cd base</code>
5. <code>./configure</code>
6. <code>make</code>
7. <code>sudo make install</code>
8. <code>sudo /opt/local/bin/port -v selfupdate</code>
9. <code>sudo port upgrade --enforce-variants</code> (Did not work for me)
10. <code>sudo port upgrade outdated</code> (Did not work for me)


[1]: http://trac.macports.org/post/macports-180-now-available/
[2]: http://distfiles.macports.org/MacPorts/MacPorts-1.8.0-10.6-SnowLeopard.dmg
[3]: http://developer.apple.com/mac/