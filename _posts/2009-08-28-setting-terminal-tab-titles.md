---

layout: post
title: "Setting terminal tab titles"
---

I've always hated the fact that I would have 5-10 tabs open in Terminal, and they would all say `bash`.

![Mac Terminal Example](http://tech.karbassi.com/images/posts/2009-08-28/screen1.png "Mac Terminal Example")

After doing some quick research, I stumbled on [decent solution](http://pseudogreen.org/blog/set_tab_names_in_leopard_terminal.html) on setting window and tab names in the Leopard Terminal.

You can add the following code block to either your `.bash_profile` or `.bashrc`.

```bash
function set\_window\_and\_tab\_title
{
local title="$1"
if \[\[ -z "$title" \]\]; then
title="root"
fi

local tmpdir=~/Library/Caches/${FUNCNAME}\_temp
local cmdfile="$tmpdir/$title"

\# Set window title
echo -n -e "\\e\]0;${title}\\a"

\# Set tab title
if \[\[ -n ${CURRENT\_TAB\_TITLE\_PID:+1} \]\]; then
kill $CURRENT\_TAB\_TITLE\_PID
fi
mkdir -p $tmpdir
ln /bin/sleep "$cmdfile"
"$cmdfile" 10 &
CURRENT\_TAB\_TITLE\_PID=$(jobs -x echo %+)
disown %+
kill -STOP $CURRENT\_TAB\_TITLE\_PID
command rm -f "$cmdfile"
}

PROMPT\_COMMAND='set\_window\_and\_tab\_title "${PWD\#\#\*/}"'
```

![Shell settings](http://tech.karbassi.com/images/posts/2009-08-28/screen2.png "Shell settings")

Restart bash and everything should be working, hunky-dory. One problem you'll notice is that when you try to close a session, terminal will prompt you about running processes. This is a side-affect of forking the process. A quick fix is to set the `"Prompt before closing"` in `Preferences > Settings > Shell` to "Never".
