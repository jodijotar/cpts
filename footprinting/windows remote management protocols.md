
- Remote Desktop Protocol (`RDP`)
- Windows Remote Management (`WinRM`)
- Windows Management Instrumentation (`WMI`)

--- RDP ---
	This protocol allows display and control commands to be transmitted via the GUI encrypted over IP networks.
	RDP works at the application layer in the TCP/IP reference model, typically utilizing TCP port 3389
	However, the connectionless UDP protocol can use port 3389 also for remote administration.

footprinting
```
nmap -sV -sC <ip> -p3389 --script rdp*
```

RDP security check
```
sudo cpan
cpan[1]> install Encoding::BER
```
```
git clone https://github.com/CiscoCXSecurity/rdp-sec-check.git && cd rdp-sec-check
```
```
./rdp-sec-check.pl <ip>
```

RDP session
```
xfreerdp /u:cry0l1t3 /p:"P455w0rd!" /v:10.129.201.248
```

--- WinRM ---
	is a simple Windows integrated remote management protocol based on the command line.
	uses the Simple Object Access Protocol (`SOAP`) to establish connections to remote hosts and their applications
	WinRM relies on `TCP` ports `5985` and `5986` for communication, with the last port `5986 using HTTPS`

footprinting
```
nmap -sV -sC <ip> -p5985,5986 --disable-arp-ping -n
```

powershell
```
evil-winrm -i 10.129.201.248 -u Cry0l1t3 -p P455w0rD!
```

--- WMI ---
	Microsoft's implementation and also an extension of the Common Information Model (`CIM`), core functionality of the standardized Web-Based Enterprise Management (`WBEM`) for the Windows platform. WMI allows read and write access to almost all settings on Windows systems
	The initialization of the WMI communication always takes place on `TCP` port `135`
	and after the successful establishment of the connection, the communication is moved to a random port
	For example, the program [wmiexec.py](https://github.com/SecureAuthCorp/impacket/blob/master/examples/wmiexec.py) from the Impacket toolkit can be used for this

footprinting
```
/usr/share/doc/python3-impacket/examples/wmiexec.py
Cry0l1t3:"P455w0rD!"@10.129.201.248 "hostname"
```





