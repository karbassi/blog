---
title: "Build tmux on CentOS 7"
date: 2019-05-29
---

If you need to install tmux 2.8 or tmux 2.9 on CentOS 7, here's the quick way to get it installed.

```bash
cd /tmp
sudo yum remove -y tmux
git clone https://github.com/tmux/tmux.git
cd tmux
git checkout 2.9a
sudo yum install -y libevent-devel ncurses-devel automake
sh autogen.sh
./configure && make
sudo make install
cd -
tmux -V
```

## Breakdown

Move to `/tmp` directory since we don't really care about where we download the source file.

```bash
cd /tmp
```

Remove previously installed tmux

```bash
sudo yum remove -y tmux
```

Download source from GitHub.

```bash
git clone https://github.com/tmux/tmux.git
```

Move into source directory

```bash
cd tmux
```

Check out current stable version. Change `2.9a` to whatever version is most current at the time.

```bash
git checkout 2.9a
```

Install `libevent`, `ncurses`, and `automake` as they are requirements.

```bash
sudo yum install -y libevent-devel ncurses-devel automake
```

Run `autogen.sh`.

```bash
sh autogen.sh
```

Configure, make, and install.

```bash
./configure && make
sudo make install
```

Go back to previous directory.

```bash
cd -2
```

Check tmux version.

```bash
tmux -V
```
