---
layout: post
title: "Firefox & Input Field Width"
date: 2009-05-26
---

Hate the 2 pixel difference you get when you apply a width on your input fields in Firefox?

Try this in CSS:

```css
input, textarea, select { -moz-box-sizing: border-box; }
```
