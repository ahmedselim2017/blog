---
type: "post"
title: "castorsCTF20 - Amazon"
author: "tozkoparan (Ahmed Selim Üzüm) & Zeyd"
tags: ["writeup", "crypto", "castorsCTF20"]
---

<!--more-->


## Amazon
Description gaves two hints. One is ```prime``` other is ```series```. Write a script to divide every number to the prime number which has the same index.

```python
import string

numbers = ['198', '291', '575', '812',
           '1221', '1482', '1955', '1273',
           '1932', '2030', '3813', '2886',
           '1968', '4085', '3243', '5830',
           '5900', '5795', '5628', '3408',
           '7300', '4108', '10043', '8455',
           '6790', '4848', '11742', '10165',
           '8284', '5424', '14986', '6681',
           '13015', '10147', '7897', '14345',
           '13816', '8313', '18370', '8304',
           '19690', '22625']

primes = ["2","3","5","7",
           "11","13","17","19",
           "23","29","31","37",
           "41","43","47","53",
           "59","61","67","71",
           "73","79","83","89",
           "97","101","103","107",
           "109","113","127","131",
           "137","139","149","151",
           "157","163","167","173",
           "179","181"]

parts = []

for i in range(len(numbers)):
    parts.append(int(numbers[i]) // int(primes[i]))

flag = ""
for part in parts:
    print(chr(part), end="")
```

**Flag:** castorsCTF{N0_End_T0d4y_F0r_L0v3_I5_X3n0n}
