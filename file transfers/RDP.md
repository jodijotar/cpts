(Remote Desktop Protocol)

mouting a linux folder in xfreerdp
```
xfreerdp /v:10.10.10.132 /d:HTB /u:administrator /p:'Password0@' /drive:linux,/home/kali/Desktop/rdp_session
```

mouting a linux folder in rdesktop
```
rdesktop 10.10.10.132 -d HTB -u administrator -p 'Password0@' -r disk:linux='/home/kali/Desktop/rdesktop'
```

Alternatively, from Windows, the native [mstsc.exe](https://docs.microsoft.com/en-us/windows-server/administration/windows-commands/mstsc) remote desktop client can be used.

notes:
	- This drive is not accessible to any other users logged on to the target computer, even if they manage to hijack the RDP session.
	- This redirected drive is tied directly to your specific RDP **session**. It is not a permanent network share on the target machine
	- if the machine has Windows Defender enabled. Sharing directories that contain any type of malware might prompt Windows Defender to delete those files on your local machine.