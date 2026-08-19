
flags
	-sn   - disables port scanning
	-oA target   - stores the results in all formats
	-iL   -  performs defined scans against targets in provided list
	-PE   - performs the ping scan by using 'ICMP Echo requests' against the target
	-Pn  - disable ICMP echo requests
	-n   - disable dns resolution
	--disable-arp-ping
	--packet-trace   - shows all packets sent and received
	--reason   - displays the reason for specific result
	-p   - define the ports
		use -p- to scan all the ports
	--top-ports=10   - define the number of top ports to be scanned
	-F   - fast scan which contains top 100 ports
	-sT   - uses TCP three-way handshake to determine if a specific port is open or closed
		not the most stealthy, but the "polite" one
	-sS   - SYN scan, half-open scan
	-sU   - UDP scan
	-sV   - identify versions and services names (banner grabbing)
	--stats-every=5s   - shows the progress of the scan every 5 sec
	-v / -vv   - show us the open ports directly when nmap detects them (output verbose)
	-sC   - default scripts
	-O   -  OS detection
	-A   - agressive scan: runs multiple flags and scripts like -sV, -O, --tracerout and -sC
	-T <0-5>   - the agressiveness of our scans, the defeault is 3
		-T 0 / -T paranoid
		-T 1 / -T sneaky
		-T 2 / -T polite
		-T 3 / -T normal
		-T 4 / -T agressive
		-T 5 / -T insane
	-f   - add delay between probes
	-sA   - TCP ACK scan method, much harder to filter for firewalls and IDS/IPS systems than regular SYN (-sS) or connect scans (-sT) - because they only send a TCP packet with only ACK flag
	-D RND:5   - decoys, generates five random IP that indicates the source IP the connection comes from - make source attribution less obvious in logs or IDS alerts
	-S   - manually specify the source IP address - usefull to bypass firewalls rules that only allow specific subnets probes
	--source-port 53   - If the administrator uses the firewall to control this port and does not filter IDS/IPS properly, our TCP packets will be trusted and passed through

advanced performance flags
	-T <0-5>   - the agressiveness of our scans
	--min-parallelism  _number_
	--max-rtt-timeout  _time_   - when nmap sends a packet it takes some time (Round-Trip-Time - RTT) to receive a response), nmap starts with a high timeout of 100ms
	--initial-rtt-timeout 50ms
	--min-rate  _number_   - how many packets should be sent simultaneously
	--max-retries  _number_   - default value is 10, we can reduce it to `0`, this means if nmap does not receive a response for a port, it won't send any more packets to that port and will skip it
	-oN tnet.minrate300 --min-rate 300    - if we know the network bandwidth, we can work with the rate of packets sent, which significantly speeds up our scans

[[nmap scripting engine (NSE)]]
[[firewall and IDS evasion]]

Style sheets
	`xsltproc nmap_output.xml -o nmap_output.html`

more info about port scanning techniques: 
	https://nmap.org/book/man-port-scanning-techniques.html
	[[Tcpdump]]
more info about performance:
	https://nmap.org/book/man-performance.html
more info about timming:
	https://nmap.org/book/performance-timing-templates.html