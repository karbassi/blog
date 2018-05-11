---
layout: post
title: "Change default editor"
---

There is a quick way to change your default editor, whichever you want.

First open up a `terminal` by going to `Applications > Accessories > Terminal` (in Ubuntu) or press `Alt + F2` and type in `terminal`. Now that you have a terminal open, let's get down to viewing your history.

Open up `.bashrc` by typing:

```bash
vim ~/.bashrc
```

Now to change your bash default editor find.

```bash
export EDITOR
```

However, if you can't find that, just add this to the top.

```bash
export EDITOR=vim
```

Personally I like `vim`. You can use `pico` (`/usr/bin/pico`), `nano` (`/usr/bin/nano`), or any other editor you like.

Like always, you can learn more about this by doing the following:

```bash
man bash
```
