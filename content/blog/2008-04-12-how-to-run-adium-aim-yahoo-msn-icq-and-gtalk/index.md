---
title: "How to run Adium (AIM, Yahoo, MSN, ICQ, and  GTalk) behind a firewall"
date: 2008-04-12
---

Being that not all locations allow all ports to be accessed through their gateway to the internet, sometimes you will run into problems in connecting to your <abbr title="Instant Messaging">IM</abbr> programs such as [iChat] or, even better, [Adium]. The following steps should work for [Pidgin].

Now, we know that all internet access points (WiFi spots, hotels, etc) will allow Port 80. This is because it is the port most web servers output websites. You can see what other ports are used for on Wikipedia's [List of TCP and UDP port] numbers page.

So, we're going to switch our Adium to connect through 80 and 443 (secure HTTP, or HTTPS as most refer to it as).

### AIM

![Adium AIM]

Let's start with the most common messenger, AIM . Set the **port to 443** and the server should be the default for your application. At the time of this it is **login.oscar.aol.com**.

### YIM

![Adium YIM]

For Yahoo, set the **port to 80** and login server to **scs.msg.yahoo.com**.

### MSN

![Adium MSN]

For MSN , set the **port to 80** and the login server to **messenger.hotmail.com**. Also check the "**Connect via HTTP**" box. This allows access through port 80.

### Google Talk

![Adium GTalk]

For Google Talk, or I'd imagine any Jabber network, set the Transport Layer Security. Also be sure to check **"Force old-style SSL"** and **"Require SSL/TLS"**. If you check "Do strict certificate checks", you will get a message box every time you try to load up Adium to accept a certificate. I have left this on, but I do know for a fact if you uncheck this, that message will not bother you again.

### ICQ

![Adium ICQ]

Lastly, if you are still using ICQ, you can set your **port to 443** and login server to **login.oscar.aol.com**. I wouldn't suggest using ICQ anymore because it's a pretty ~bad~ old service. Check out the [criticisms on wikipedia].

Now, if you restart your Adium (or whatever client you are using), you should have connection to the IM protocols.

### Draw backs

Some of the drawbacks to this method is that your data is being sent over an unsecured port, and therefore can be subject to any sniffers. If you are paranoid about your chats, I'd suggest using an online version such as [Meebo] which does go through HTTPS.

[ichat]: http://www.apple.com/macosx/features/ichat.html
[adium]: http://www.adiumx.com/
[pidgin]: http://www.pidgin.im/
[list of tcp and udp port]: http://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers
[adium aim]: ./AdiumAIM.jpg "Adium AIM"
[adium yim]: ./AdiumYIM.jpg "Adium YIM"
[adium msn]: ./AdiumMSN.jpg "Adium MSN"
[adium gtalk]: ./AdiumGTalk.jpg "Adium GTalk"
[adium icq]: ./AdiumICQ.jpg "Adium ICQ"
[criticisms on wikipedia]: http://en.wikipedia.org/wiki/ICQ#Criticism
[meebo]: http://www.meebo.com/
