---
layout: post
title: "How To FULLY Disable Spotlight in Leopard"
date: 2009-05-12
---

**Warning:** This is changing system settings that may or may not be attached to other tools. After an extensive search on the internet, one of these tools affected by the following steps is [TimeMachine] / [TimeCapsule]. If you are using them, I would **not** follow these steps. Rule of thumb: if you think it will mess up your system and you don't want to worry about that, don't do it.

### Quick way

#### Disable:

```bash
sudo launchctl unload -w "/System/Library/LaunchDaemons/com.apple.metadata.mds.plist"
sudo launchctl unload -w "/System/Library/LaunchAgents/com.apple.Spotlight.plist"
```

#### re-enable:

```bash
sudo launchctl load -w "/System/Library/LaunchDaemons/com.apple.metadata.mds.plist"
sudo launchctl load -w "/System/Library/LaunchAgents/com.apple.Spotlight.plist"
```

### Explanation

#### Stop and disable the background server:

##### Kill the Daemon:

```bash
sudo launchctl unload -w "/System/Library/LaunchDaemons/com.apple.metadata.mds.plist"
```

##### Re-enable the Daemon:

```bash
sudo launchctl load -w "/System/Library/LaunchDaemons/com.apple.metadata.mds.plist"
```

#### Stop and disable the spotlight application itself:

##### Kill the Agent:

```bash
sudo launchctl unload -w "/System/Library/LaunchAgents/com.apple.Spotlight.plist"
```

##### Re-enable the Agent:

```bash
sudo launchctl load -w "/System/Library/LaunchAgents/com.apple.Spotlight.plist"
```

You may get an error on the last command; just ignore it.

### What it does

We stop the process from running and tell the system to fully disable it.

```bash
sudo launchctl unload -w "/System/Library/LaunchDaemons/com.apple.metadata.mds.plist"
```

Now we need to stop the agent for the user and everyone else.

```bash
sudo launchctl unload -w "/System/Library/LaunchAgents/com.apple.Spotlight.plist"
```

### The re-enable Spotlight back again:

If you need to re-enable the process, you can run the following line.

```bash
sudo launchctl load -w "/System/Library/LaunchDaemons/com.apple.metadata.mds.plist"
```

The following line re-enable the Spotlight agent.

```bash
sudo launchctl load -w "/System/Library/LaunchAgents/com.apple.Spotlight.plist"
```

The reason you get the error is that you are effectively executing the command as root, but the root user hasn't any running instance of Spotlight. On the other hand, only the root user is able to disable the automatic start of Spotlight. Thus the need for the `sudo` command.

Done!

There's no need to reboot your computer after following these steps.

[TimeMachine]: http://www.apple.com/macosx/features/timemachine.html
[TimeCapsule]: http://www.apple.com/timecapsule/
