---
type: "post"
title: "castorsCTF20 - Leftovers"
author: "tozkoparan (Ahmed Selim Üzüm)"
tags: ["writeup", "forensics", "castorsCTF20"]
---

<!--more-->
We can decode the packages using this code
The packages are `USB` packages. So maybe it is a keyboard? We can find decoding information
indside HID Usage Tables. So let's decode it using python.

```python
from scapy.all import *

newmap = {
    0: "",
    2: "PostFail",
    4: "a",
    5: "b",
    6: "c",
    7: "d",
    8: "e",
    9: "f",
    10: "g",
    11: "h",
    12: "i",
    13: "j",
    14: "k",
    15: "l",
    16: "m",
    17: "n",
    18: "o",
    19: "p",
    20: "q",
    21: "r",
    22: "s",
    23: "t",
    24: "u",
    25: "v",
    26: "w",
    27: "x",
    28: "y",
    29: "z",
    30: "1",
    31: "2",
    32: "3",
    33: "4",
    34: "5",
    35: "6",
    36: "7",
    37: "8",
    38: "9",
    39: "0",
    40: "Enter",
    41: "esc",
    42: "del",
    43: "tab",
    44: " ",
    45: "-",
    47: "{",
    48: "}",
    56: "/",
    57: "CapsLock",
    79: "RightArrow",
    80: "LetfArrow"
}

packets = rdpcap('./interrupts.pcapng')

for p in packets:
    try:
        s_byte = hex(p[0].load[-6])
        #print(s_byte)
        print(newmap[int(s_byte, 16)],end="")
    except:
        continue

```

```
cwhat dooyoo  thhnng yyuu will ffnnn herr/ thhss/ csstossCapsLockctfCapsLock{1stiswhatyoowant}
```
And we get something like a flag. So let's clean and find the real flag!



**Flag:** `castorsCTF{1stiswhatyoowant}`
