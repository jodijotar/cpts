## ssh keys

python script to acquire the corresponding hash
```
ssh2john.py SSH.private > ssh.hash
```

john the reaper to crack the hash
```
john --wordlist=rockyou.txt ssh.hash
```
---

## office documents

microsoft office
```
office2john.py Protected.docx > protected-docx.hash
```

pdf
```
pdf2john.py PDF.pdf > pdf.hash
```

offline cracking
```
john --wordlist=rockyou.txt document.hash
```
 ---

## bitlocker encrypted disks

get the hash
```
bitlocker2john -i Backup.vhd > backup.hashes
```

# mounting

setup
```
sudo apt-get install dislocker
```

directories to mount
```
jodijotar@htb[/htb]$ sudo mkdir -p /media/bitlocker
jodijotar@htb[/htb]$ sudo mkdir -p /media/bitlockermount
```

we then use `losetup` to configure the VHD as [loop device](https://en.wikipedia.org/wiki/Loop_device), decrypt the drive using `dislocker`, and finally mount the decrypted volume
```
jodijotar@htb[/htb]$ sudo losetup -f -P Backup.vhd
jodijotar@htb[/htb]$ sudo dislocker /dev/loop0p2 -uPassword! -- /media/bitlocker
jodijotar@htb[/htb]$ sudo mount -o loop /media/bitlocker/dislocker-file /media/bitlockermount
```

after getting the interesting files, unmount:
```
jodijotar@htb[/htb]$ sudo umount /media/bitlockermount
jodijotar@htb[/htb]$ sudo umount /media/bitlocker
```
---


