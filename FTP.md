FTP (File Transfer Protocol), which use port TCP/21 and TCP/20

Installing the FTP Server Python3 Module - pyftpdlib
```
sudo pip3 install pyftpdlib
```

setting up the ftp server:
```
sudo python3 -m pyftpdlib --port 21
```

transferring files from an FTP Server with PowerShell
```
PS C:\htb> (New-Object Net.WebClient).DownloadFile('ftp://192.168.49.128/file.txt', 'C:\Users\Public\ftp-file.txt')
```

