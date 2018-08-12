---
layout: post
title: "Safari 3.1 and Pith Helmet"
date: 2008-03-19
---

Recently Apple updated their browser Safari to version 3.1. It does boast new features that us web developers love, but it also crashes some hacks we also love. Note that I’m not calling them "plug-ins". Read the [reasoning behind this].

Now, one of my favorite Safari hacks has been Pith Helmet and with the
new update, it is considered "broken."

### Here’s how to fix it:

1. Quit Safari.

2. Navigate to `/Library/Application Support/SIMBL/Plugins/PithHelmet.bundle.`

3. Control click to show package contents.

4. Open bundle and go to Contents.

5. Double click or open `info.plist` in your favorite text editor.

6. Change `MaxBundleVersion` to `5525.13`. This is to match the current Safari version/build.

    ```xml
    <key>MaxBundleVersion</key>
    <string>5525.13</string>
    ```

7. Save and relaunch Safari.

[reasoning behind this]: http://daringfireball.net/2007/10/un_in_unsupported
