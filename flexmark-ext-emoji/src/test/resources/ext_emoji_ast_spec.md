---
title: Emoji Extension Spec
author: Vladimir Schneider
version: 0.1
date: '2016-06-06'
license: '[CC-BY-SA 4.0](http://creativecommons.org/licenses/by-sa/4.0/)'
...

---

## Emoji

Converts :warning: to its emoji image

```````````````````````````````` example Emoji: 1
:warning:
.
<p><img src="/img/warning.png" alt="emoji places:warning" /></p>
.
Document[0, 10]
  Paragraph[0, 10]
    Emoji[0, 9] textOpen:[0, 1, ":"] text:[1, 8, "warning"] textClose:[8, 9, ":"]
      Text[1, 8] chars:[1, 8, "warning"]
````````````````````````````````


Should work in links

```````````````````````````````` example Emoji: 2
[:warning:](/url)
.
<p><a href="/url"><img src="/img/warning.png" alt="emoji places:warning" /></a></p>
.
Document[0, 18]
  Paragraph[0, 18]
    Link[0, 17] textOpen:[0, 1, "["] text:[1, 10, ":warning:"] textClose:[10, 11, "]"] linkOpen:[11, 12, "("] url:[12, 16, "/url"] pageRef:[12, 16, "/url"] linkClose:[16, 17, ")"]
      Emoji[1, 10] textOpen:[1, 2, ":"] text:[2, 9, "warning"] textClose:[9, 10, ":"]
        Text[2, 9] chars:[2, 9, "warning"]
````````````````````````````````


```````````````````````````````` example(Emoji: 3) options(url)
:warning:
.
<p><img src="https://assets-cdn.github.com/images/icons/emoji/unicode/26a0.png" alt="emoji places:warning" /></p>
.
Document[0, 10]
  Paragraph[0, 10]
    Emoji[0, 9] textOpen:[0, 1, ":"] text:[1, 8, "warning"] textClose:[8, 9, ":"]
      Text[1, 8] chars:[1, 8, "warning"]
````````````````````````````````


Should work in links

```````````````````````````````` example Emoji: 4
[:warning:](/url)
.
<p><a href="/url"><img src="/img/warning.png" alt="emoji places:warning" /></a></p>
.
Document[0, 18]
  Paragraph[0, 18]
    Link[0, 17] textOpen:[0, 1, "["] text:[1, 10, ":warning:"] textClose:[10, 11, "]"] linkOpen:[11, 12, "("] url:[12, 16, "/url"] pageRef:[12, 16, "/url"] linkClose:[16, 17, ")"]
      Emoji[1, 10] textOpen:[1, 2, ":"] text:[2, 9, "warning"] textClose:[9, 10, ":"]
        Text[2, 9] chars:[2, 9, "warning"]
````````````````````````````````


Unknown shortcuts are converted to text

```````````````````````````````` example Emoji: 5
:warnings:
.
<p>:warnings:</p>
.
Document[0, 11]
  Paragraph[0, 11]
    Emoji[0, 10] textOpen:[0, 1, ":"] text:[1, 9, "warnings"] textClose:[9, 10, ":"]
      Text[1, 9] chars:[1, 9, "warnings"]
````````````````````````````````


Unknown shortcuts are converted to text with inline emphasis parsing

```````````````````````````````` example Emoji: 6
:**warnings**:
.
<p>:<strong>warnings</strong>:</p>
.
Document[0, 15]
  Paragraph[0, 15]
    Emoji[0, 14] textOpen:[0, 1, ":"] text:[1, 13, "**warnings**"] textClose:[13, 14, ":"]
      StrongEmphasis[1, 13] textOpen:[1, 3, "**"] text:[3, 11, "warnings"] textClose:[11, 13, "**"]
        Text[3, 11] chars:[3, 11, "warnings"]
````````````````````````````````

