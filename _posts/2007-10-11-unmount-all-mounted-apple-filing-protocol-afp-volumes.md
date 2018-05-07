---

layout: post
title: "Unmount all mounted Apple Filing Protocol (AFP) volumes"
---

I travel from location to location, jumping from one wireless access point to another. While I love my mac, but I've always hated that it stalls whenever I reconnect to a wireless network because I didn't unmount my AFP (Apple Filing Protocol)s before disconnecting. The operating system would give me the [spinner of death](http://en.wikipedia.org/wiki/Spinning_wait_cursor) for a few minutes before it stopped.

I set out to fix this problem. More after the break.

First, I wrote a script that will unmount all AFP mounts.

```bash
\#\!/bin/bash
\#

1.  Unmount all Apple Filing Protocol (AFP) volumes that are currently
2.  mounted
    \#
3.  Version 1.0
    \#
4.  Date Written: 2007-10-11
5.  Last Modified: 2007-10-11 02:03 PM (14:03)
    \#
6.  © Copyright 2007 Ali Karbassi.
7.  Released under the GPL license
8.  http://www.gnu.org/copyleft/gpl.html

if \[ \`df | grep 'afp' | wc -l | sed 's| ||g'\` \!= '0' \]
then
umount $(df | grep 'afp' | sed 's|.\* /|/|')
fi
```

Save the above to any location. I have a folder in my user directory called Scripts, so this file is located at '`~/Scripts/unmountAllAFP.sh`'. Be sure to `chmod +x` this file. You can do this like so:

```bash
chmod +x unmountAllAFP.sh
```

Then you will need to install [SleepWatcher](http://www.bernhard-baehr.de/) (current version as of now is 2.0.4).

After this is installed, load up terminal and follow along.

```bash
cd ~
touch .sleep
chmod 0700 .sleep
mate .sleep
```

Note that I use [TextMate](http://macromates.com/). You can replace `mate` with `nano`.

Once you have the `.sleep` file open, add the absolute location of the script you want to run when your mac goes to sleep. For this example, we want our unmounting script to run. You should have the following in the file.

```bash
~/Scripts/unmountAllAFP.sh
```

That's it. This will run every-time your mac goes to sleep.
