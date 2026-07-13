SMB (server message block) commands are transmitted over Samba to an older NetBIOS service, connections typically occur over TCP ports `137`, `138`, and `139`. In contrast, CIFS (common internet file system) operates over TCP port `445` exclusively.

---- Manual enumeration

listing an accessible share
```
smbclient -N -L //<ip>
```

connecting to the share
```
smbclient //<ip>/<accessible_share>
```

RPC client - doc: https://www.samba.org/samba/docs/current/man-html/rpcclient.1.html
```
rpcclient -U "" <ip>
```

RPC enumeration
```
srvinfo
enumdomains
querydominfo
netshareenumall
netsharegetinfo <accessible_share>
```


---- Automated enumeration
enumeration tools
```
https://github.com/fortra/impacket/blob/master/examples/samrdump.py
```
```
smbmap -H <ip>
```
```
crackmapexec smb <ip> --shares -u '' -p ''
```


enum4linux-ng
	based on an older tool, enum4linux. This tool automates many of the queries, return a large amount of information.
	-installation
```
git clone https://github.com/cddmp/enum4linux-ng.git
cd enum4linux-ng
pip3 install -r requirements.txt
```

```
./enum4linux-ng.py <ip> -A
```


