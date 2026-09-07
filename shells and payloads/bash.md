/bin/bash flags
	-i (interactive)
		gives you an proper command prompt and enables features like job control -> interactive shell
	-c (command)
		tells bash to execute a command that is provided as a string
	-p (privileged)
		key for privilege escalation: if you find a bash binary on a system that has the SUID bit set, running it may drop its privileges. the -p flag tells bash to not drop these privileges -> root shell
	-s (read from stdin)
		tells bash to read commands from stdin

logic operators
	 AND ( && )
		only runs the next command if the previous command runs succefully
	OR ( | | )
		only runs the next command if the previous command fails

command chaining
	semicolon ( ; )
		lets us run multiple commands **sequentially** in one line
		no matter what happens to the previous command, it will run the next
	pipe ( | )
		redirects the stdout stream from the first command diretly to the expected stdin stream for the next command
	ampersand ( & )
		runs a command in the background allowing us to use the terminal without waiting the command finish, after the program runs the output is printed on the terminal

[[bypassing waf - OS commands]]
[[staying away from disk]]

