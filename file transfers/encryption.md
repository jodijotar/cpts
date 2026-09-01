## windows

import module Invoke-AESEEncryption.ps1
```
PS C:\htb> Import-Module .\Invoke-AESEncryption.ps1
```

use example
```
PS C:\htb> Invoke-AESEncryption -Mode Encrypt -Key "p4ssw0rd" -Path .\scan-results.txt
```

---
## linux

encrypting
```
openssl enc -aes256 -iter 100000 -pbkdf2 -in /etc/passwd -out passwd.enc
```

decrypt
```
openssl enc -d -aes256 -iter 100000 -pbkdf2 -in passwd.enc -out passwd
```