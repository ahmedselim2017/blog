---
type: "post"
title: "Reverse-me"
author: "tozkoparan (Ahmed Selim Üzüm)"
tags: ["writeup", "reversing", "castorsCTF20"]
---

It looks like we can get flag but it is encoded. Normally, I should have reversed
the binary and find how it encode the flag and the decode it and get the flag. But
I first tested all printable chars and get the corresponding encoded byte. Then
with that, I matched all encoded bytes to corresponding char and got the flag

**Flag:** `castorsCTF{r3v3r51n6_15_fun}`
