---
layout: post
title: "Create a list of installed packages"
date: 2007-01-21
---

Ever wanted to know what applications are actually installed on your system? Sure you can view the applications via the applications bar, but there are so many other applications not shown there.

Also, what if you have your system with all the applications you want and want to install them again on another PC (or after a reinstall)? [Cynical] shows us how to do that with a few simple steps.

To output this information to a file in your home directory you would use:

```bash
dpkg --get-selections > installed-software
```

**Note:** `installed-software` is actually just a text file. You can open it to view it, but don't modify it if you don't know what you're doing. It might screw up the next step.

If you wanted to use the list to reinstall this software on a fresh Ubuntu setup or on another computer, just do the following steps:

```bash
dpkg --set-selections < installed-software
dselect
sudo apt-get autoremove
sudo apt-get autoclean
```

[Cynical]: http://ubuntuforums.org/showthread.php?t=261366
