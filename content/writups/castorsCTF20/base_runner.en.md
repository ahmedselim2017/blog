---
type: "post"
title: "Base castorsCTF20 - Number"
author: "tozkoparan (Ahmed Selim Üzüm)"
tags: ["writeup", "coding", "castorsCTF20"]
---

<!--more-->
For getting the flag in this challenge we should first decode the given binary
from binary, then octal, then hex and then base64.

```python
from pwn import *
import base64

def decode(data):
    bin_decoded = ""
    for d in data.split(" "):
        binary = chr(int(d, 2))
        bin_decoded += binary

    oct_decoded = ""
    for s in bin_decoded.split(" "):
        oct_decoded += str(chr(int(s, 8)))

    hex_decoded = ""
    for s in oct_decoded.split(" "):
        hex_decoded += str(chr(int(s, 16)))

    return base64.b64decode(hex_sonuc).decode("ascii")


conn = remote("chals20.cybercastors.com", 14430)
conn.recvuntil("y.\n")
conn.sendline("\n")

while True:
    try:
        data = str(conn.recvline().decode("ascii"))
        print(data)
        decoded = decode(data)
        conn.sendline(decoded)
        print(conn.recvline())
    except:
        data = conn.recv(1024)
        print(data)

```

**Flag:** `castorsCTF{m4j0r_l34gu3_py7h0n_b4s3_runn3r}`
