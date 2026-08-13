[Rsync](https://linux.die.net/man/1/rsync) is a fast and efficient tool for locally and remotely copying files. It can be used to copy files locally on a given machine and to/from remote hosts. It is highly versatile and well-known for its delta-transfer algorithm.

By default, it uses port `873` and can be configured to use SSH for secure file transfers by piggybacking on top of an established SSH server connection.


scanning for rsync
```
sudo nmap -sV -p 873 127.0.0.1
```

include the `-e ssh` flag, or `-e "ssh -p2222"` if a non-standard port is in use for SSH

probing for accessible shares
```
nc -nv 127.0.0.1 873
```

enumerating an open share
```
rsync -av --list-only rsync://127.0.0.1/dev
```



