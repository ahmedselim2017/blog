---
type: "post"
title: "castorsCTF20 - Goose Chase"
author: "Zeyd"
tags: ["writeup", "crypto", "castorsCTF20"]
---


<!--more-->

Challange says it response to Amazon so it should be again about prime series.

```python
primes = ["2","3","5","7","11","13","17","19","23","29","31","37","41","43","47","53","59","61","67","71","73","79","83","89","97","101","103","107","109","113","127","131","137","139","149","151","157","163","167","173","179","181","191","193","197","199","211","223","227","229","233","239","241","251","257"]

all_ct = "198 34 61 41 193 197 156 245 133 231 215 14 70 230 33 231 221 141 219 67 160 52 119 4 127 50 19 140 201 1 101 120 95 192 20 142 51 191 188 2 33 121 225 93 211 70 224 202 238 114 194 38 56".split()

alphabet = ["}","{","c","w","e","r","t","y","u","ı","o","p","a","s","d","f","g","h","j","k","l","i","z","x","q","v","b","n","m","Q","W","E","R","T","Y","U","I","O","P","A","S","D","F","G","H","J","K","L","Z","X","C","V","B","N","M","_","1","2","3","4","5","6","7","8","9","0"]

prime = primes[0]
mod = 0x101

def bf():
        for i in range(53):
            ct = all_ct[i]
            for b in primes:
                for u in alphabet:
                    if ord(u) * int(b) % mod == int(ct):
                        if primes.index(b) == i:
                            print(u, end="")

bf()
```

**Flag:** `castorsCTF{1f_y0u_g07_th1s_w1th0u7_4ny_h1n7s_r3sp3c7}`
