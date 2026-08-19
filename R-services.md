span across the ports `512`, `513`, and `514` and are only accessible through a suite of programs known as `r-commands`

| command | service daemon | port | transport protocol | description                                                                                                                   |
| ------- | -------------- | ---- | ------------------ | ----------------------------------------------------------------------------------------------------------------------------- |
| rcp     | rshd           | 514  | TCP                | copy a file or directory. (provides no warning to the user for overwriting existing files on a system)                        |
| rsh     | rshd           | 514  | TCP                | opens a shell without a login procedure. relies upon the trusted entries in /etc/hosts.equiv and .rhosts files for validation |
| rexec   | rexecd         | 512  | TCP                | enables a user to run shell commands. requires authentication through an unencrypted network socket.                          |
| rlogin  | rlogind        | 513  | TCP                | enables a user to log in to a remote host over the network.                                                                   |
Scanning for R-Services
```
sudo nmap -sV -p 512,513,514 10.0.17.2
```

By default, these services utilize [Pluggable Authentication Modules (PAM)](https://web.archive.org/web/20241102161436/https://debathena.mit.edu/trac/wiki/PAM) for user authentication onto a remote system; however, they also bypass this authentication through the use of the `/etc/hosts.equiv` and `.rhosts` files on the system. 

The `hosts.equiv` and `.rhosts` files contain a list of hosts (`IPs` or `Hostnames`) and users that are `trusted` by the local host when a connection attempt is made using `r-commands`

