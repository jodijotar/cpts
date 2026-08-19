simple mail transfer protocol

by default, SMTP servers accept connection requests on port `25`. However, newer SMTP servers also use other ports such as TCP port `587`. Under certain circumstances, a server uses a port other than the standard TCP port `25` for the encrypted connection, for example, TCP port `465`

at the beginning of the connection, authentication occurs when the client confirms its identity with a user name and password

| Command    | Description                                                                                      |
| ---------- | ------------------------------------------------------------------------------------------------ |
| AUTH PLAIN | AUTH is a service extension used to authenticate the client.                                     |
| HELO       | The client logs in with its computer name and thus starts the session.                           |
| MAIL FROM  | The client names the email sender.                                                               |
| RCPT TO    | The client names the email recipient.                                                            |
| DATA       | The client initiates the transmission of the email.                                              |
| RSET       | The client aborts the initiated transmission but keeps the connection between client and server. |
| VRFY       | The client checks if a mailbox is available for message transfer.                                |
| EXPN       | The client also checks if a mailbox is available for messaging with this command.                |
| NOOP       | The client requests a response from the server to prevent disconnection due to time-out.         |
| QUIT       | The client terminates the session.                                                               |

to interact with the SMTP server, we can use the `telnet` tool to initialize a TCP connection with the SMTP server. The actual initialization of the session is done with the command mentioned above, `HELO` or `EHLO`.

```
telnet <ip> <port>
```

The command `VRFY` can be used to enumerate existing users on the system.
```
smtp-user-enum -M VRFY -U /usr/share/seclists/Usernames/top-usernames-shortlist.txt -t <ip> -v -w20
```

Open Relay Configuration
```
mynetworks = 0.0.0.0/0
```
With this setting, this SMTP server can send fake emails and thus initialize communication between multiple parties. Another attack possibility would be to spoof the email and read it.

footprinting the service
```
sudo nmap <ip> -sC -sV -p25
```

we can also use the [smtp-open-relay](https://nmap.org/nsedoc/scripts/smtp-open-relay.html) NSE script to identify the target SMTP server as an open relay using 16 different tests.
```
sudo nmap <ip> -p25 --script smtp-open-relay -v
```

example:
```
jodijotar@root$ telnet 10.129.14.128 25

Trying 10.129.14.128...
Connected to 10.129.14.128.
Escape character is '^]'.
220 ESMTP Server


EHLO inlanefreight.htb

250-mail1.inlanefreight.htb
250-PIPELINING
250-SIZE 10240000
250-ETRN
250-ENHANCEDSTATUSCODES
250-8BITMIME
250-DSN
250-SMTPUTF8
250 CHUNKING


MAIL FROM: <cry0l1t3@inlanefreight.htb>

250 2.1.0 Ok


RCPT TO: <mrb3n@inlanefreight.htb> NOTIFY=success,failure

250 2.1.5 Ok


DATA

354 End data with <CR><LF>.<CR><LF>

From: <cry0l1t3@inlanefreight.htb>
To: <mrb3n@inlanefreight.htb>
Subject: DB
Date: Tue, 28 Sept 2021 16:32:51 +0200
Hey man, I am trying to access our XY-DB but the creds don't work. 
Did you make any changes there?
.

250 2.0.0 Ok: queued as 6E1CF1681AB


QUIT

221 2.0.0 Bye
Connection closed by foreign host.
```

list of response codes - https://serversmtp.com/smtp-error/?doing_wp_cron=1785267541.6900010108947753906250
The structure of an email header is defined by - https://datatracker.ietf.org/doc/html/rfc5322