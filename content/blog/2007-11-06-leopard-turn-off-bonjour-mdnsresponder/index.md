---
title: "Leopard: Turn off Bonjour (mDNSResponder)"
date: 2007-11-06
---

> **Update**: [jaqkar] noted in the comments that this does not work in Snow Leopard and because of good reason. As stated in the Apple Support Document [Mac OS X v10.6: Disabling mDNSResponder will disable DNS], "Mac OS X v10.6 uses the mDNSResponder process for unicast DNS (Domain Name System) functions, as well as Bonjour functions. Disabling the mDNSResponder process will also disable unicast DNS resolution, and without unicast DNS resolution, Mac OS X v10.6 cannot resolve hostnames such as www.apple.com." On Apple's Support site, there are instructions to disable Bonjour if need be.

I recently upgrades to Leopard and the operating system has been great. After installing my core set of programs, I noticed that [mDNSResponder] was going nuts. Being that I am on an university network, there are hundreds on the current sub-network. By default, Leopard has a "feature" that lists all the local computers (windows or mac) that it finds. This is called [Bonjour] You may know about this via [iChat], or other programs. Sure, that's nice, but does it take up _lots_ processes. Again, this would be nice upon request, but the task is done repeatedly. The load on your system just gets out of hand.

After some research, I found that there is a Launch Daemon for this. Here's how you turn it off, but don't worry, you can turn it back on anytime, without restarts or anything.

Load up Terminal (`Applications > Utilities > Terminal.app`) and type the following.

```bash
sudo launchctl unload -w /System/Library/LaunchDaemons/com.apple.mDNSResponder.plist
```

To turn it back on, just do the opposite:

```bash
sudo launchctl load -w /System/Library/LaunchDaemons/com.apple.mDNSResponder.plist
```

[jaqkar]: http://tech.karbassi.com/2007/11/06/leopard-turn-off-bonjour-mdnsresponder/#comment-38183328
[mac os x v10.6: disabling mdnsresponder will disable dns]: http://support.apple.com/kb/HT3789
[mdnsresponder]: http://developer.apple.com/opensource/internet/bonjour.html
[bonjour]: http://en.wikipedia.org/wiki/Bonjour_%28software%29
[ichat]: http://www.apple.com/ichat/
