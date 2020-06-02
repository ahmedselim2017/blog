---
type: "post"
title: "castorsCTF20 - Stack"
author: "tozkoparan (Ahmed Selim Üzüm)"
tags: ["writeup", "reversing", "castorsCTF20"]
---

<!--more-->
First we should inspect the binary id `radare2`

```
λ › r2 -d stacking
[0x7fe5bbd5b100]> aaa
[0x7fe5bbd5b100]> afl
[0x7fe5bbd5b100]> s main
[0x5630d16b870a]> pdf
            ; DATA XREF from entry0 @ 0x5630d16b861d
┌ 32: int main (int argc, char **argv, char **envp);
│           ; var int64_t var_10h @ rbp-0x10
│           ; var int64_t var_4h @ rbp-0x4
│           ; arg int argc @ rdi
│           ; arg char **argv @ rsi
│           0x5630d16b870a      55             push rbp
│           0x5630d16b870b      4889e5         mov rbp, rsp
│           0x5630d16b870e      4883ec10       sub rsp, 0x10
│           0x5630d16b8712      897dfc         mov dword [var_4h], edi ; argc
│           0x5630d16b8715      488975f0       mov qword [var_10h], rsi ; argv
│           0x5630d16b8719      b800000000     mov eax, 0
│           0x5630d16b871e      e807000000     call sym.func
│           0x5630d16b8723      b800000000     mov eax, 0
│           0x5630d16b8728      c9             leave
└           0x5630d16b8729      c3             ret
```

We can see there is a mysterious function called `sym.func`. Let's inspect it.

```
[0x5630d16b870a]> s sym.func
[0x5630d16b872a]> pdf
│           0x5630d16b8741      c645c063       mov byte [var_40h], 0x63 ; 'c' ; 99
│           0x5630d16b8745      c645c161       mov byte [var_3fh], 0x61 ; 'a' ; 97
│           0x5630d16b8749      c645c273       mov byte [var_3eh], 0x73 ; 's' ; 115
│           0x5630d16b874d      c645c374       mov byte [var_3dh], 0x74 ; 't' ; 116
│           0x5630d16b8751      c645c46f       mov byte [var_3ch], 0x6f ; 'o' ; 111
│           0x5630d16b8755      c645c572       mov byte [var_3bh], 0x72 ; 'r' ; 114
│           0x5630d16b8759      c645c673       mov byte [var_3ah], 0x73 ; 's' ; 115
│           0x5630d16b875d      c645c743       mov byte [var_39h], 0x43 ; 'C' ; 67
│           0x5630d16b8761      c645c854       mov byte [var_38h], 0x54 ; 'T' ; 84
│           0x5630d16b8765      c645c946       mov byte [var_37h], 0x46 ; 'F' ; 70
│           0x5630d16b8769      c645ca7b       mov byte [var_36h], 0x7b ; '{' ; 123
│           0x5630d16b876d      c645cb77       mov byte [var_35h], 0x77 ; 'w' ; 119
│           0x5630d16b8771      c645cc33       mov byte [var_34h], 0x33 ; '3' ; 51
│           0x5630d16b8775      c645cd6c       mov byte [var_33h], 0x6c ; 'l' ; 108
│           0x5630d16b8779      c645ce63       mov byte [var_32h], 0x63 ; 'c' ; 99
│           0x5630d16b877d      c645cf30       mov byte [var_31h], 0x30 ; '0' ; 48
│           0x5630d16b8781      c645d06d       mov byte [var_30h], 0x6d ; 'm' ; 109
│           0x5630d16b8785      c645d133       mov byte [var_2fh], 0x33 ; '3' ; 51
│           0x5630d16b8789      c645d25f       mov byte [var_2eh], 0x5f ; '_' ; 95
│           0x5630d16b878d      c645d337       mov byte [var_2dh], 0x37 ; '7' ; 55
│           0x5630d16b8791      c645d430       mov byte [var_2ch], 0x30 ; '0' ; 48
│           0x5630d16b8795      c645d55f       mov byte [var_2bh], 0x5f ; '_' ; 95
│           0x5630d16b8799      c645d672       mov byte [var_2ah], 0x72 ; 'r' ; 114
│           0x5630d16b879d      c645d733       mov byte [var_29h], 0x33 ; '3' ; 51
│           0x5630d16b87a1      c645d876       mov byte [var_28h], 0x76 ; 'v' ; 118
│           0x5630d16b87a5      c645d933       mov byte [var_27h], 0x33 ; '3' ; 51
│           0x5630d16b87a9      c645da72       mov byte [var_26h], 0x72 ; 'r' ; 114
│           0x5630d16b87ad      c645db35       mov byte [var_25h], 0x35 ; '5' ; 53
│           0x5630d16b87b1      c645dc33       mov byte [var_24h], 0x33 ; '3' ; 51
│           0x5630d16b87b5      c645dd5f       mov byte [var_23h], 0x5f ; '_' ; 95
│           0x5630d16b87b9      c645de33       mov byte [var_22h], 0x33 ; '3' ; 51
│           0x5630d16b87bd      c645df6e       mov byte [var_21h], 0x6e ; 'n' ; 110
│           0x5630d16b87c1      c645e036       mov byte [var_20h], 0x36 ; '6' ; 54
│           0x5630d16b87c5      c645e131       mov byte [var_1fh], 0x31 ; '1' ; 49
│           0x5630d16b87c9      c645e26e       mov byte [var_1eh], 0x6e ; 'n' ; 110
│           0x5630d16b87cd      c645e333       mov byte [var_1dh], 0x33 ; '3' ; 51
│           0x5630d16b87d1      c645e433       mov byte [var_1ch], 0x33 ; '3' ; 51
│           0x5630d16b87d5      c645e572       mov byte [var_1bh], 0x72 ; 'r' ; 114
│           0x5630d16b87d9      c645e631       mov byte [var_1ah], 0x31 ; '1' ; 49
│           0x5630d16b87dd      c645e76e       mov byte [var_19h], 0x6e ; 'n' ; 110
│           0x5630d16b87e1      c645e836       mov byte [var_18h], 0x36 ; '6' ; 54
│           0x5630d16b87e5      c645e97d       mov byte [var_17h], 0x7d ; '}' ; 125
```

**Flag:** `castorsCTF{w3lc0m3_70_r3v3r53_3n61n33r1n6}`
