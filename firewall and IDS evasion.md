
find open ports
```
nmap <target> -sS -Pn -n --disable-arp-ping -D RND:5
```

specific port scanning - using udp combined with SYN scan through DNS port
```
nmap <target> -sS -Pn -sV -p 53 -n --disable-arp-ping --source-port 53 -sU
```

some services discovered using port 53 as source, can only be connected using the same port. for more info like version and banners, you can do the complete tcp connection manually using netcat
```
ncat -nv --source 10.10.15.112 --source-port 53 <target> 50000
```