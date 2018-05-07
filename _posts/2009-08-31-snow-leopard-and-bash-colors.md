---

layout: post
title: "Snow Leopard and Bash Colors"
---

One little problem people—including myself—have been running into is bash color codes. Many `.bashrc` files have the following (or similar):

```bash
export COLOR\_NC='\\e\[0m' \# No Color
export COLOR\_WHITE='\\e\[1;37m'
export COLOR\_BLACK='\\e\[0;30m'
export COLOR\_BLUE='\\e\[0;34m'
export COLOR\_LIGHT\_BLUE='\\e\[1;34m'
export COLOR\_GREEN='\\e\[0;32m'
export COLOR\_LIGHT\_GREEN='\\e\[1;32m'
export COLOR\_CYAN='\\e\[0;36m'
export COLOR\_LIGHT\_CYAN='\\e\[1;36m'
export COLOR\_RED='\\e\[0;31m'
export COLOR\_LIGHT\_RED='\\e\[1;31m'
export COLOR\_PURPLE='\\e\[0;35m'
export COLOR\_LIGHT\_PURPLE='\\e\[1;35m'
export COLOR\_BROWN='\\e\[0;33m'
export COLOR\_YELLOW='\\e\[1;33m'
export COLOR\_GRAY='\\e\[1;30m'
export COLOR\_LIGHT\_GRAY='\\e\[0;37m'
```

The solution is to use `\033` as the escape code rather than `\e`.

```bash

1.  Setup some colors to use later in interactive shell or scripts
    export COLOR\_NC='\\033\[0m' \# No Color
    export COLOR\_WHITE='\\033\[1;37m'
    export COLOR\_BLACK='\\033\[0;30m'
    export COLOR\_BLUE='\\033\[0;34m'
    export COLOR\_LIGHT\_BLUE='\\033\[1;34m'
    export COLOR\_GREEN='\\033\[0;32m'
    export COLOR\_LIGHT\_GREEN='\\033\[1;32m'
    export COLOR\_CYAN='\\033\[0;36m'
    export COLOR\_LIGHT\_CYAN='\\033\[1;36m'
    export COLOR\_RED='\\033\[0;31m'
    export COLOR\_LIGHT\_RED='\\033\[1;31m'
    export COLOR\_PURPLE='\\033\[0;35m'
    export COLOR\_LIGHT\_PURPLE='\\033\[1;35m'
    export COLOR\_BROWN='\\033\[0;33m'
    export COLOR\_YELLOW='\\033\[1;33m'
    export COLOR\_GRAY='\\033\[1;30m'
    export COLOR\_LIGHT\_GRAY='\\033\[0;37m'
    ```
