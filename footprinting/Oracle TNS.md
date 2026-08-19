`Oracle Transparent Network Substrate` (`TNS`)

listens for incoming connections on the `TCP/1521` port

The configuration files for Oracle TNS are called `tnsnames.ora` and `listener.ora` and are typically located in the `$ORACLE_HOME/network/admin` directory

Footprinting
```
sudo nmap -p 1521 -sV --open 10.129.14.222
```
```
sudo nmap -p 1521 -sV --open --script=oracle-sid-brute 10.129.14.222
```