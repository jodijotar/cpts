
IMAP (`Internet Message Access Protocol`)
POP3 (`Post Office Protocol`)

By default, ports `110` and `995` are used for POP3, and ports `143` and `993` are used for IMAP

Immediately after the connection is established, the user is authenticated by user name and password to the server.

IMAP commands

| Command                     | Description                                                                                              |
| --------------------------- | -------------------------------------------------------------------------------------------------------- |
| LOGIN username password     | user's login                                                                                             |
| LIST "" *                   | lists all directories                                                                                    |
| CREATE "INBOX"              | creates a mailbox with a specified name                                                                  |
| DELETE "INBOX"              | deletes a mailbox                                                                                        |
| RENAME "ToRead" "Important" | renames a mailbox                                                                                        |
| LSUB "" *                   | returns a subset of names from the set of names that the user has declared as being active or subscribed |
| SELECT INBOX                | selects a mailbox so that messages in the mailbox can be accessed                                        |
| UNSELECT INBOX              | exits the selected mailbox                                                                               |
| FETCH `<ID>` all            | retrieves data associated with a message in the mailbox                                                  |
| CLOSE                       | removes all messages with the deleted flag set                                                           |
| LOGOUT                      | closes the connection with the IMAP server                                                               |

POP3 commands

| Command       | Description                                                |
| ------------- | ---------------------------------------------------------- |
| USER username | identifies the user                                        |
| PASS password | authentication of the user                                 |
| STAT          | requests the number of saved emails from the server        |
| LIST          | requests from the server the number and size of all emails |
| RETR id       | requests the server to deliver the requested email by ID   |
| DELE id       | requests the server to delete the requested email by ID    |
| CAPA          | requests the server to display the server capabilities     |
| RSET          | requests the server to reset the transmitted information   |
| QUIT          | closes the connection with the POP3 server                 |

footprinting
```
sudo nmap <ip> -sV -p110,143,993,995 -sC
```
```
curl -k 'imaps://10.129.14.128' --user cry0l1t3:1234 -v
```

OpenSSL - TLS Encrypted Interaction POP3
```
openssl s_client -connect 10.129.14.128:pop3s
```
OpenSSL - TLS Encrypted Interaction IMAP
```
openssl s_client -connect 10.129.14.128:imaps
```

