---
type: "post"
title: "castorsCTF20 - Two Paths"
author: "Zeyd"
tags: ["writeup", "crypto", "castorsCTF20"]
---

<!--more-->

![Two path](/writups/castorsctf20/two-paths.png)


Using `strings` on the image and it gives us a binary.

```
01101000 01110100 01110100 01110000 01110011 00111010 00101111 00101111 01100111 01101111 00101110 01100001 01110111 01110011 00101111 00110010 01111010 01110101 01000011 01000110 01000011 01110000 
```
When decode it gaves this link:
```
https://go.aws/2zuCFCp
```
Where we can find a lot of random emojies like:
```
♈♓♒🌀🔁♉❌🈲♏♉❌⏺♓♒♊!_⏺💯_🔟♓🈲_♈♉♒_🔁✖♉⛎_❌⏫⏺♊,_❌⏫✖♒_🔟♓🈲_⏫♉➗✖_♊♓♏➗✖⛎_❌⏫✖_♈⏺♑⏫✖🔁!_🚺✖_➿🈲♊❌_⏫♓♑✖_🔟♓🈲_💯♓🈲♒⛎_♉_Ⓜ♓🔁✖_✖💯💯⏺♈⏺✖♒❌_🚺♉🔟_💯♓🔁_⛎✖♈⏺♑⏫✖
```
Need to decode this but to decode it we need more. So return to the image and `stegsolve` on it. When we change the color settings the hidden link appear in the left bottom corner. The page is named `decode-this` .
```
https://go.aws/2X1R6H7
```
In this there is a chat between two people. One is texting and other only using emojies. Guessed some of the words that the second person said eg. `hi! ` and `you?`. By using these letters found all alphabet in emojies. 
```
♉: A
♌: B
♈: C
⛎: D
✖ : E
💯: F
🌀: G
⏫: H
⏺: I
🆔: K
♏: L
Ⓜ: M
♒: N
♓: O
♑: P
🔁: R
♊: S
❌: T
🈲: U
🔟: Y
📶: Z
🚺: W
🔴: X
```
Then search castorsCTF by using emoji alpahbet in the `decode-this` website.

**Flag:** `castorsCTF{sancocho_flag_qjzmlpg}`
