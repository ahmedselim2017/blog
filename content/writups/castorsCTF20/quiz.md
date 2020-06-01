---
type: "post"
title: "Quiz"
author: "tozkoparan (Ahmed Selim Üzüm)"
tags: ["writeup", "web", "castorsCTF20"]
---

It looks like there is some math problems in here. Let's use gobuster for finding
is there anything else. We found `backup`! And ther is an interesting function called
super which prints a file. So let's print the flag. But where could it be? maybe
inside `/home/$USER/flag.txt`? Let's try it. We know the user is `jeff` from challenge
description. Let's send a request to `http://web1.cybercastors.com:14436/test/home/jeff/flag.txt`
And we got the flag!

**Flag:** `castorsCTC{wh0_l4iks_qUiZZ3s_4nyW4y}`
