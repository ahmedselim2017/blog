---
type: "post"
title: "castorsCTF20 - One Tricky Pony"
author: "Zeyd"
tags: ["writeup", "crypto", "castorsCTF20"]
---

<!--more-->

It returns hex values when entered random characters. Then try to enter some spaces in it. And then it gives:
```
b'CASTORSctf[K\x13\x13P\x7fY\x10UR\x7fK\x13Y\x15\x7f\x15\x13CR\x13\x17\x7f\x14ND\x7fD\x10N\x17\x7fR\x13U\x15\x13\x7f\x17H\x13M\x01]
```

By using the [ASCII Table](https://bluesock.org/~willg/dev/ascii.html) and manually decode every hex value.

**Flag:** `castorsCTF{k33p_y0ur_k3y5_53cr37_4nd_d0n7_r3u53_7h3m!}`
