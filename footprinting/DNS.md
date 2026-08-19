dns records
	A - returns ipv4 addresses for the requested domain
	AAAA - returns ipv6 addresses for the requested domain
	MX - returns the responsible main server for the requested domain
	NS - returns the authoritative name server FQDN of the domain
	TXT - contains various information, such as validated SSL certificates, google search console etc
	CNAME - this record serves as an alias for another domain name. e. g., different subdomains may point to the same domain, but are hosted by different hosts. with that, we can set an A record of that ip hosts and the same CNAME on them pointing to an domain name.
	PTR - reverse lookup -> converts ip addresses into qualified domain names (FQDN - full qualified domain name)
	SOA - provides information about the DNS zone and email addresses of the administrative contact
	AXFR - zone transfer -> **DNS zone is a database of DNS records**, and many of those records contain **FQDNs**. A zone transfer is a way to copy that database from a DNS server.

dig sintax
```
dig <query-type> <domain> @<DNS-server>
```

the DNS server can be queried as to which other name servers are known
using the NS record and the specification of the DNS server we want to query using the `@` character
```
dig ns inlanefreight.htb @10.129.14.128
```

the option `ANY` can be used to view all available records
```
dig any inlanefreight.htb @10.129.14.128
```

`Zone transfer` refers to the transfer of zones to another server in DNS, which generally happens over TCP port 53. This procedure is abbreviated `Asynchronous Full Transfer Zone` (`AXFR`)
```
dig axfr inlanefreight.htb @10.129.14.128
```

FQDNs matters when footprinting bc they tell a lot about the infrastructure behind that host, like:
```
mail.inlanefreight.htb       → mail infrastructure
vpn.inlanefreight.htb        → VPN gateway
gitlab.inlanefreight.htb     → source-code platform
jenkins.inlanefreight.htb    → CI/CD server
dev.inlanefreight.htb        → development environment
staging.inlanefreight.htb    → preproduction environment
db01.inlanefreight.htb       → database server
files.inlanefreight.htb      → file server
```

If the administrator used a subnet for the `allow-transfer` option for testing purposes or as a workaround solution or set it to `any`, everyone would query the entire zone file at the DNS server.
```
dig axfr internal.inlanefreight.htb @10.129.14.128
```

subdomain brute forcing
```
dnsenum --dnsserver 10.129.14.128 --enum -p 0 -s 0 -o subdomains.txt -f /usr/share/seclists/Discovery/DNS/subdomains-top1million-110000.txt inlanefreight.htb
```

research resources
	bind9 - https://www.cvedetails.com/product/144/ISC-Bind.html?vendor_id=64
	securitytrails - https://web.archive.org/web/20250329174745/https://securitytrails.com/blog/most-popular-types-dns-attacks