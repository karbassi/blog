--- 
layout: post
title: How to run Adium (AIM, Yahoo, MSN, ICQ, and  GTalk)
---
Being that not all locations allow all ports to be accessed through their gateway to the internet, sometimes you will run into problems in connecting to your <abbr title="Instant Messaging">IM</abbr> programs such as [iChat](http://www.apple.com/macosx/features/ichat.html) or, even better, [Adium](http://www.adiumx.com/). The following steps should work for [Pidgin](http://www.pidgin.im/).

Now, we know that all internet access points (WiFi spots, hotels, etc) will allow Port 80. This is because it is the port most web servers output websites. You can see what other ports are used for on Wikipedia's "[List of TCP and UDP port](http://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers) numbers page.

So, we're going to switch our Adium to connect through 80 and 443 (secure HTTP, or HTTPS as most refer to it as).

![Adium AIM](http://farm3.static.flickr.com/2152/2408558009_f654227f92.jpg)

Let's start with the most common messenger, <abbr title="AOL Instant Messenger">AIM</abbr>. Set the **port to 443** and the server should be the default for your application. At the time of this it is **<login.oscar.aol.com>**.

![Adium YIM](http://farm4.static.flickr.com/3294/2409393304_908c130bab.jpg)

For Yahoo, set the **port to 80** and login server to **<scs.msg.yahoo.com>**.

![Adium MSN](http://farm3.static.flickr.com/2101/2409393188_48bd4c8463.jpg)

For <acronym title="The Microsoft Network">MSN</acronym>, set the **port to 80** and the login server to **<messenger.hotmail.com>**. Also check the "**Connect via HTTP**" box. This allows access through port 80.

![Adium GTalk](http://farm4.static.flickr.com/3192/2409393356_a32833511b.jpg)

For Google Talk, or I'd imagine any Jabber network, set the Transport Layer Security. Also be sure to check **"Force old-style <abbr title="Secure Sockets Layer">SSL</abbr>"** and **"Require SSL/<acronym title="Transport Layer Security">TLS</acronym>"**. If you check "Do strict certificate checks", you will get a message box every time you try to load up Adium to accept a certificate. I have left this on, but I do know for a fact if you uncheck this, that message will not bother you again.

![Adium ICQ](http://farm4.static.flickr.com/3115/2408558179_9b734925fa.jpg)

Lastly, if you are still using ICQ, you can set your **port to 443** and login server to **<login.oscar.aol.com>**. I wouldn't suggest using ICQ anymore because it's a pretty bad service. Check out the [criticisms on wikipedia](http://en.wikipedia.org/wiki/ICQ#Criticism).

Now, if you restart your Adium (or whatever client you are using), you should have connection to the IM protocols.

Draw backs
----------

Some of the drawbacks to this method is that your data is being sent over an unsecure port, and therefore can be subject to any sniffers. If you are paranoid about your chats, I'd suggest using an online version such as [Meebo](http://www.meebo.com/) which does go through HTTPS.
