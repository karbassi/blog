---

layout: post
title: "View and Change bash history"
---

> **Update:** Fixed a typo.
> **Update:** Added grep search.

Always wanted to know what you have been doing via bash? Did you know bash keeps a history of that? Here is a quick way to check it and an easy way to change the history limit.

First open up a `terminal` by going to `Applications > Accessories > Terminal` (in Ubuntu) or press `Alt + F2` and type in `terminal`. Now that you have a terminal open, let's get down to viewing your history.

To view your history via the terminal, type:

```bash
history
```

This will show the whole list.

To view your history in a editor (to save for later), just type:

```bash
history -w ~/history.txt
vim ~/history.txt
```

What `history -w ~/history.txt` does is save the `history` to a file named `history.txt` on your home folder (`cd ~/`). The next command opens up the file for viewing in `vim`.

**Note:** For more information about `history` be sure to use the man pages by doing:

```bash
man history
```

Now to change your bash history length, just open up your `.bashrc` by doing so:

```bash
vim ~/.bashrc
```

Once open, at the top add.

```bash
export HISTFILESIZE=3000
```

As you can see, the limit can be changed.

Bash keeps it's own history in a file. You can view that file as stated before, or by opening `~/.bash_history`

You can search through your bash\_history by piping your history file into grep like so:

```bash
history | grep "search term here"
```

Example:

```bash
history | grep "wget"
```
