---
type: "post"
title: "castorsCTF20 - Password Crack 3"
author: "tozkoparan (Ahmed Selim Üzüm)"
tags: ["writeup", "misc", "castorsCTF20"]
---

<!--more-->
This one is a bit more diffrent than other password crack challenges. We can't
crack it using normal rockyou wordlist becauese it is wrapped inside flag format.
Bu we can try to brute force wrapping all the words inside rockyou. And for that
we can use python.

```python
import hashlib

flag_hash = "7adebe1e15c37e23ab25c40a317b76547a75ad84bf57b378520fd59b66dd9e12"

flag_format = "castorsCTF{xxx}"

enc = 'latin-1'
rockyou = open(<path_to_rockyou>, encoding=enc)
for line in rockyou:
    rock = line.strip("\n")
    flag = flag_format.replace("xxx", rock).encode()
    n_hash = hashlib.sha256()
    n_hash.update(flag)
    if n_hash.hexdigest() == flag_hash:
        print("flag: " + flag.decode())
        break
    else:
        continue

```

**Flag:** `castorsCTF{theformat!}`
