---
layout: post
title: "See how many Kernel Panics your Mac has had"
date: 2009-05-26
---

In bash:

```bash
ls -1 /Library/Logs/PanicReporter/ | wc -l
```

or

```bash
ls -1 /Library/Logs/DiagnosticReports/ | wc -l
```


I've had *5*.
