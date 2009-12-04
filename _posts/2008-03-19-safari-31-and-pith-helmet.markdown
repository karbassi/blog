--- 
layout: post
title: Safari 3.1 and Pith Helmet
---
Recently Apple updated their browser Safari to version 3.1. It does boast new features that us web developers love, but it also crashes some hacks we also love. Note that I'm not calling them "plug-ins". Read the [reasoning behind this](http://daringfireball.net/2007/10/un_in_unsupported).

Now, one of my favorite Safari hacks has been Pith Helmet and with the new update, it is considered "broken." 

**Here's how to fix it:**

1. Quit Safari.
2. Navigate to <tt>/Library/Application Support/SIMBL/Plugins/PithHelmet.bundle.</tt>
3. Control click to show package contents.
4. Open bundle and go to Contents.
5. Double click or open <tt>info.plist</tt> in your favorite text editor.
6. Change <tt>MaxBundleVersion</tt> to <tt>5525.13</tt>. This is to match the current Safari version/build.

    &lt;key&gt;MaxBundleVersion&lt;/key&gt;
    &lt;string&gt;5525.13&lt;/string&gt;

7. Save and relaunch Safari.