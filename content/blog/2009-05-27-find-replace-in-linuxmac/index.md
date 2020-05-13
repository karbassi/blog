---
title: "Find & Replace in Linux/Mac"
date: 2009-05-27
---

This is a quick one liner to find and replace strings in \*nix. You can use this in your Mac terminal or Unix prompt.

In Bash:

```bash
find . -type f -exec sed -i 's/FIND/REPLACE/g' {} \;
```

Example:

```bash
find . -type f -exec sed -i 's/signin/login/g' {} \;
```
