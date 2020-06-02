---
type: "post"
title: "castorsCTF20 - Gif"
author: "tozkoparan (Ahmed Selim Üzüm)"
tags: ["writeup", "misc", "castorsCTF20"]
---

<!--more-->
![Gif](/writups/castorsctf20/gif.gif)

We can extract the numbers we see with `convert -coalesce brocoli.gif gif.gif`
command.

To extract numbers, there are a ton of tools out there, but I just used
`convert -coalesce chal.gif chal.png`.

Numbers: `15 13 7 19 15 6 21 14 14 25 12 15 12`

Then I used `cyberchef` for guessing which kind of cipher is it
![cyberchef](/writups/castorsctf20/gif_cyberchef.png)

With adding `_` to between words and wrapping it in flag format we should get the flag.

**Flag:** `castorsCTF{omg_so_funny_lol}`
