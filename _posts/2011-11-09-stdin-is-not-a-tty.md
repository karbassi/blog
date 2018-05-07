---

layout: post
title: "Solving 'stdin: is not a tty' error"
---

The "stdin: is not a tty" warning kept on popping up when `ssh`-ing to a few servers. I've learned that the problem is because I had `mesg n` on top of my `.bash_rc` file. Quick fix is to wrap it around an if statement, like so:

```bash
if \`tty -s\`; then
mesg n
fi
```
