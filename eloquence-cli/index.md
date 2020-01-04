# ELOC

雄辩的命令行

---

## Prior Arts

- [slides.com](https://slides.com) beautiful & full-featured

- [mdx-deck](https://github.com/jxnblk/mdx-deck) markdown + react

---

# FOCUS

on __writing__, not __styling__

---

### Problem with `mdx-deck`

Big / Buggy / Slow

[![install size](https://badgen.net/packagephobia/install/mdx-deck?scale=2)](https://packagephobia.now.sh/result?p=mdx-deck)

---

### WEBR Loop

```c
Watch - Edit - Build - Refresh
  <- build process
    <- mdx with react
      <- never used react
```

---

### An Express Version

- No build, no react

- Install in __seconds__, start in __milliseconds__

---

### Meet `eloc`

---

A markdown presentation authoring cli  
for presenters who

1. __focus__ on writing
2. present in a __concise__ style

---

`npm install eloc`

```bash
# Serve "deck.md" as presentation
$ eloc deck.md

# Create & serve "new-deck.md" as presentation
$ eloc new-deck.md

# Export presentation with images
$ eloc build deck.md --include "*.jpg"
```

---

### Markdown PPT ABC

```c
 # Title

 ----

 ## Chapter 1

 The first rule of Fight Club is: You do not talk about Fight Club.

 ----

 # The End
```

---

## Shortcuts

prev / next <kbd>left</kbd> / <kbd>right</kbd>

first / last <kbd>up</kbd> / <kbd>down</kbd>

---

## PRINT VIEW

★ <kbd>P</kbd> ★

---

## DARK MODE

★ <kbd>D</kbd> ★

---

## THE EDITOR

★ <kbd>ESC</kbd> ★

---

## Customization

```
_write style tag within markdown_

<style>
  .slide { background: url(...) }
  .content { filter: invert() }
  code { opacity: 0.8 }
</style>
```

<style>
.slide {
  background: url(https://el-capitan.now.sh) center;
  background-size: cover;
}
.content { filter: invert() }
code { opacity: 0.8 }
</style>

---

## Demo Time

---

#### "True __eloquence__,<br /> does not consist in saying great things<br/> in a sublime style,

---

#### but in a simple style."

_-- Oliver Goldsmith_

---

try it now

## `npm i eloc`