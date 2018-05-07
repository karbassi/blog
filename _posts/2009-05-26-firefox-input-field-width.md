---

layout: post
title: "Firefox & Input Field Width"
---

Hate the 2 pixel difference you get when you apply a width on your input fields in Firefox?

Try this in CSS:

```css
input, textarea, select{-moz-box-sizing: border-box;}
```