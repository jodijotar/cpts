#services

When footprinting NFS, the TCP ports `111` and `2049` are essential. We can also get information about the NFS service and the host via RPC

scanning ports 111 and 2049
```
nmap <ip> -p111,2049 -sV -sC
```

the `rpcinfo` NSE script retrieves a list of all currently running RPC services, their names and descriptions, and the ports they use. This lets us check whether the target share is connected to the network on all required ports. Also, for NFS, Nmap has some NSE scripts that can be used for the scans.
```
nmap --script nfs* <ip> -sV -p111,2049
```

show available NFS shares
```
showmount -e <ip>
```

once we have discovered such an NFS service, we can mount it on our local machine. For this, we can create a new empty folder to which the NFS share will be mounted
```
jodijotar@root$ mkdir target-NFS
jodijotar@root$ sudo mount -t nfs <ip>:/ ./target-NFS/ -o nolock
jodijotar@root$ cd target-NFS
jodijotar@root$ tree .
```

list contents with Usernames & Group names
```
ls -l mnt/nfs/
```

list contents with UIDs & GUIDs
```
ls -n mnt/nfs/
```

after we have done all the necessary steps and obtained the information we need, we can unmount the NFS share.
```
umount ./target-NFS
```
