### Linux

in cases of an firewall preventing us from dowloading a file from our machine, we can use this trick:

```
jodijotar@root$ base64 <file-name> -w 0
```

now we copy this base64 string, paste in to the remote host and use `base64 -d` to decode it
```
user@remotehost$ echo f0VMRgIBAQAAAAAAAAAAAAIAPgABAAAA... <SNIP> ...lIuy9iaW4vc2gAU0iJ51JXSInmDwU | base64 -d > shell

```

validating
```
user@remotehost$ file <file-name>

jodijotar@root$ md5sum <file-name>
user@remotehost$ md5sum <file-name>

```
---
### powershell

Dowload operations
base64 trick - decode to file
```
[IO.File]::WriteAllBytes("C:\Users\Public\<file_path>", [Convert]::FromBase64String("<string_base64_file>")
```

confirming MD5 hash
```
Get-FileHash C:\Users\Public\<file_path> -Algorithm md5
```

#### Upload operations
base 64 trick powershell - enconding an file
```
PS C:\htb> [Convert]::ToBase64String((Get-Content -path "C:\Windows\system32\drivers\etc\hosts" -Encoding byte))
```

