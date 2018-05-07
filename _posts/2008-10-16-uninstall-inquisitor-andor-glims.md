---

layout: post
title: "Uninstall Inquisitor and/or Glims"
---

![Schoschie vs. Apple](http://tech.karbassi.com/images/posts/2008-10-16/schoschie.jpg "Schoschie vs. Apple"):http://www.flickr.com/photos/87569910@N00/2530972208/

Recently I've giving [Glims](http://www.machangout.com/) a try. Even though it **tries** to combine what Inquisitor and Saft both do into one single free application, I was very disappointed in the ease of use and look.

Before trying Glims, I had to uninstall (remove) [Inquisitor](http://www.inquisitorx.com/safari/) that was already running on my version of [Webkit](http://www.webkit.org) and Safari. To do this, I opened up terminal and typed the following commands (with my password that is):

```bash
sudo rm -rf /Library/InputManagers/Inquisitor/
sudo rm -rf /Library/Receipts/inquisitor\*
sudo rm -rf ~/Library/Application\\ Support/Inquisitor/
```

After couple hours of use, I wanted to switch back to Inquisitor, which meant that I had to remove Glims. To do that action, I pulled up terminal, yet again, and typed the follow:

```bash
sudo rm -rf /Library/InputManagers/Glims/
sudo rm -rf ~/Library/Application\\ Support/Glims/
```

That should take care of everything, leaving my computer nice and clean.