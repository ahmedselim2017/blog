---
type: "post"
title: "castorsCTF20 - Car Lottery"
author: "tozkoparan (Ahmed Selim Üzüm)"
tags: ["writeup", "coding", "castorsCTF20"]
---

<!--more-->
First, with changing our `client` cookie to `3123248` we can access winner page.
Then we can see site is using `id` param for getting car types. And if we use
a invalid car type and then send a invalid ID we get an SQL error!

With that we can dump data (and crack) from SQL database using this command:
```shell
sqlmap -u "http://web1.cybercastors.com:14435/search?id=" --method=POST --cookie="client=3123248" --dump
```
And we got some creds! For using them we can find the `/dealer` dir using `gobuster`.
Then we can login and get the flag.

**Flag:** `castorCTF{daT4B_3n4m_1s_fuN_N_p0w3rfu7}`

