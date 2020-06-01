---
type: "post"
title: "Octopus"
author: "tozkoparan (Ahmed Selim Üzüm)"
tags: ["writeup", "reversing", "castorsCTF20"]
---


First we can see there is base64 encoded data inside PEM certificate. When we
decode it we get a executable file. Then with executing it we get some Portuguese
text and base64 encoded flag!

**Flag:** `castorsCTF{Wh0_s41d_AnY7hlnG_B0uT_m4tH}`
