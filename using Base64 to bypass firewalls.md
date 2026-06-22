#transfering_files

in cases of an firewall preventing us from dowloading a file from our machine, we can use this trick:

```
jodijotar@root$ base64 shell -w 0
```

now we copy this base64 string, paste in to the remote host and use `base64 -d` to decode it
```
user@remotehost$ echo f0VMRgIBAQAAAAAAAAAAAAIAPgABAAAA... <SNIP> ...lIuy9iaW4vc2gAU0iJ51JXSInmDwU | base64 -d > shell

```

validating
```
user@remotehost$ file shell

jodijotar@root$ md5sum shell
user@remotehost$ md5sum shell

```