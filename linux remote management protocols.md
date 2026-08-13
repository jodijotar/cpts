[Secure Shell](https://en.wikipedia.org/wiki/Secure_Shell) (`SSH`)

enables two computers to establish an encrypted and direct connection within a possibly insecure network on the standard port `TCP 22`

ssh default configuration
```
cat /etc/ssh/sshd_config  | grep -v "#" | sed -r '/^\s*$/d'
```

Footprinting
SSH-audit
```
git clone https://github.com/jtesta/ssh-audit.git && cd ssh-audit
```
```
./ssh-audit.py 10.129.14.132
```

[[Rsync]]
[[R-services]]

