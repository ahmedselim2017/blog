---
type: "post"
title: "castorsCTF20 - Warmup"
author: "tozkoparan (Ahmed Selim Üzüm)"
tags: ["writeup", "crypto", "castorsCTF20"]
---

<!--more-->

With some calculations we can get `p` and `q`

{{<sup a 2>}} + {{<sup b 2>}} = {{<sup c 2>}}

{{<sup "(p + q)" 2>}} + {{<sup "(p - q)" 2>}} = {{<sup c 2>}}

{{<sup 2p 2>}} + {{<sup 2q 2>}} = {{<sup c 2>}}

---

ab = 2A

(p + q) (p - q) = 2A

{{<sup p 2>}} - {{<sup q 2>}} = 2A

---

{{<sup 2p 2>}} - {{<sup 2q 2>}} = 4A

{{<sup 2p 2>}} + {{<sup 2q 2>}} = {{<sup c 2>}}

{{<sup 4p 2>}} = 4A + {{<sup c 2>}}

And we got the `p`! Now we can get `q` easily with plugging `p` into one of the
equation. So let's compute them!

```python
import gmpy2
c_square = 41027546415588921135190519817388916847442693284567375482282571314638757544938653824671437300971782426302443281077457253827782026089649732942648771306702020
A=1780602199528179468577178612383888301611753776788787799581979768613992169436352468580888042155360498830144442282937213247708372597613226926855391934953064

p = int(gmpy2.isqrt(c_square + 4 * A) // 2)
q = int(gmpy2.isqrt(p**2 - 2 * A))
print("p: {}".format(p))
print("q: {}".format(q))
```

Now let's decrypt the message!
```python
from Crypto.Util.number import inverse

n = p * q
e=0x10001
enc=825531027337680366509171870396193970230179478931882005355846498785843598000659828635030935743236266080589740863128695174980645084614454653557872620514117

phi = (p -1) * (q - 1)
d = inverse(e, phi)

m = pow(enc, d, n)
print((hex(m))[2:-1].decode('hex'))
```

**Flag:** `castorsCTF{n0th1ng_l1k3_pr1m3_numb3r5_t0_w4rm_up_7h3_3ng1n3s}`



