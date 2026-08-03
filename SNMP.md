`Simple Network Management Protocol`

it is a protocol for monitoring and managing network devices. In addition, configuration tasks can be handled, and settings can be made remotely using this standard
In addition to the pure exchange of information, SNMP also transmits control commands using agents over UDP port `161`

SNMP also enables the use of so-called `traps` over UDP port `162`. These are data packets sent from the SNMP server to the client without being explicitly requested

SNMP Daemon Config
```
cat /etc/snmp/snmpd.conf | grep -v "#" | sed -r '/^\s*$/d'
```

For footprinting SNMP, we can use tools like `snmpwalk`, `onesixtyone`, and `braa`. `Snmpwalk` is used to query the OIDs with their information. `Onesixtyone` can be used to brute-force the names of the community strings

SNMPwalk
```
snmpwalk -v2c -c public <ip>
```

we can use `onesixtyone` and `SecLists` wordlists to identify these community strings.
OneSixtyOne
```
sudo apt install onesixtyone
```
```
onesixtyone -c /opt/useful/seclists/Discovery/SNMP/snmp.txt <ip>
```

Often, when certain community strings are bound to specific IP addresses, they are named with the hostname of the host, and sometimes even symbols are added to these names to make them more challenging to identify
We can use the tool [crunch](https://secf00tprint.github.io/blog/passwords/crunch/advanced/en) to create custom wordlists.

Once we know a community string, we can use it with [braa](https://github.com/mteg/braa) to brute-force the individual OIDs
```
sudo apt install braa
```
```
braa <community string>@<ip>:.1.3.6.*
```

