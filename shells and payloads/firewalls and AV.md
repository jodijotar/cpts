### payloads

we usually don't need to reivent the wheel when it comes to payloads, but some sys admins are aware of open source resources that pentesters use.

these repos often are the core considerations of what to expect in an attack.
so in some cases, we may need to customize our shell code a bit.

understanding what different types of payloads are doing can help us understand why AV is blocking us from execution and give us some idea of what we might need to change in our code to bypass restrictions

---
### common ports

It would be rare to see any security team blocking 443 outbound since many applications and organizations rely on HTTPS to get to various websites
but, a firewall capable of deep packet inspection and Layer 7 visibility may be able to detect & stop a reverse shell going outbound on a common port because it's examining the contents of the network packets, not just the IP address and port
