---
type: "post"
title: "castorsCTF20 - Manipulation"
author: "tozkoparan (Ahmed Selim Üzüm)"
tags: ["writeup", "forensics", "castorsCTF20"]
---

<!--more-->
We can see pooh.jpg is a `hexdump` of a file and we can reverse it using `xxd -r pooh.jph pooh`.
And when we checked file type using `file` command get a data? Maybe there was no
header? Let's add one and open it! We got the flag!

**Flag:** `castorsCTF{H3r3_Is_y0uR_Fl4gg}`
