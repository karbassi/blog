---
title: "Command, Option, & Shift Symbols in Unicode"
date: 2009-05-27
---

> **Update:** Ratty in the comment noted that &\#x238B; is actually the ESC key button not the power button.
>
> **Update 2012:** Added more symbols.

Unicode does define some other characters which are sort of Mac-specific.

| Character | Entity Code | Entity Name | Description               |
| --------- | ----------- | ----------- | ------------------------- |
| ⌘         | `&#x2318`   | `&#8984`    | Command Key symbol        |
| ⌥         | `&#x2325`   | `&#8997`    | Option Key symbol         |
| ⇧         | `&#x21E7`   | `&#8679`    | Shift Key symbol          |
| ⎋         | `&#x238B`   | `&#9099`    | ESC Key symbol            |
| ⇪         | `&#x21ea`   | `&#8682`    | Capslock symbol           |
| ⏎         | `&#x23ce`   | `&#9166`    | Return symbol             |
| ⌫         | `&#x232b`   | `&#9003`    | Delete / Backspace symbol |

**Note:** The Power Button and Shift Key are not Mac-specific. The power button is described as "broken circle with northwest arrow", or an escape character from ISO 9995-7. The shift key is described as an "outline up-arrow".

Even though these are defined in standard Unicode, there is **no guarantee** that they will exist in the font of the receiving browser, but they’re at least globally defined, so they’re fair game.
