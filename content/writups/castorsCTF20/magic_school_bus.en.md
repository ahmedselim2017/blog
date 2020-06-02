---
type: "post"
title: "castorsCTF20 - Magic School Bus"
author: "Zeyd"
tags: ["writeup", "crypto", "castorsCTF20"]
---

<!--more-->

There is two options. The second one gives the flag with changing the order and making them uppercase. This was the given flag:
```
SCNTGET0SKV3CTNESYS2ISL7AF4I0SC0COM5ORS31RR3AYN1
```
And in the first option change the given letter to uppercase and it you write multiple character it change the order. Need to find how it change the order. To find it gave it 46 char lenght of string that has not same char in it. 
```
Input:
ABCDEFTGHIJKLMNOPRSTVYZXWQÖÇÜĞŞİ1234567890€₺½¾
Output:
TNZŞ7DKTÇ4½AHPW19CJSÖ3€BIRQ20GOİ8ELVÜ5¾FMYĞ6₺
```
Then check and note how it change the order by each index. Then apply by reversely on the given flag.

**Flag:**: `CASTORSCTF{R3C0N4ISSANCE_IS_K3Y_TO_S0LV1NG_MYS73R1E5}`
