---
title: "Remove temp folder contents on shutdown"
date: 2007-01-14
---

A few days ago Codejacked wrote an article talking about [Delete your TEMP files on shutdown] for Windows. As much as I loved the article, I have recently switched over to [Ubuntu]. Like all operating systems, GNU Linux has temporary files also. Here's how to delete them on shutdown.

1. Back up what you're going to working on.

   ```bash
   sudo cp /etc/init.d/sysklogd /etc/init.d/sysklogd_backup
   ```

2. Open the file in `vim`

   ```bash
   sudo vim /etc/init.d/sysklogd
   ```

3. Find the following section

   ```bash
   # ...
   stop)
   log_begin_msg "Stopping system log daemon..."
   start-stop-daemon --stop --quiet --oknodo --exec $binpath --pidfile $pidfile
   log_end_msg $?
   # ...
   ```

4. Add the following line after `log_end_msg $?` or before `;;`.

   ```bash
   rm -fr /tmp/* /tmp/.??*
   ```

5. Save the file and you're set!

[delete your temp files on shutdown]: http://www.codejacked.com/delete-your-temp-files-on-shutdown/
[ubuntu]: http://www.ubuntu.com
