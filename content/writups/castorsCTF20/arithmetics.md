---
type: "post"
title: "Arithmetics"
author: "tozkoparan (Ahmed Selim Üzüm)"
tags: ["writeup", "Coding", "castorsCTF20"]
---

When we connect to the server, we can see we have to answer a lot of questions.
So that let's write a script!

```python
from pwn import *

conn = remote("chals20.cybercastors.com",14429)
conn.recvuntil("<")
conn.recvuntil("\n")
conn.send("\n")
sayilar = {"one":1,
        "two":2,
        "three":3,
        "four":4,
        "five":5,
        "six":6,
        "seven":7,
        "eight":8,
        "nine":9,
        "zero":0}

while True:
    try:
        soru =  conn.recvline()
        print(soru)
        soru = str(soru).split(" ")
        try:
            sayi1 = int(soru[2])
        except:
            sayi1 = sayilar[soru[2]]

        try:
            sayi2 = int(soru[4])
        except:
            sayi2 = sayilar[soru[4]]

        if soru[3] == '+' or soru[3] == "plus":
            islem = "+"
            sonuc = sayi1 + sayi2
        elif soru[3] == '-' or soru[3] == "minus":
            islem = "-"
            sonuc = sayi1 - sayi2
        elif soru[3] == '*' or soru[3] == "multiplied-by":
            islem = "*"
            sonuc = sayi1 * sayi2
        elif soru[3] == '//' or soru[3] == "divided-by":
            islem = "/"
            sonuc = sayi1 // sayi2

        conn.sendline(str(sonuc) + "\n")
        print(sonuc, "-"*10)
        print(conn.recvline())
    except:
        data = conn.recv(1024)
        print(data)
```

**Flag:** `castorsCTF(n00b_pyth0n_4r17hm3t1c5}`
