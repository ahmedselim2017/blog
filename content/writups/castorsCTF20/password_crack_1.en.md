---
type: "post"
title: "castorsCTF20 - Password Crack 1"
author: "tozkoparan (Ahmed Selim Üzüm)"
tags: ["writeup", "misc", "castorsCTF20"]
---

<!--more-->
If we want to crack a hash we have to know what type is it. For that I used `hashid`
and learned that the type of hash is `md5`. Then I used a website called crackstation
for cracking md5 hash.

And we should get the flag by wrapping the result of the hash in flag format

**Flag:** `castorsCTF{irocktoo}`
