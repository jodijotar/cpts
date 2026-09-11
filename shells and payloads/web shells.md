/usr/share/webshells/

when attempting to gain a shell session with a target, it would be wise to establish a reverse shell and then delete the executed payload

 Laudanum - various payloads
	files can be found in the `/usr/share/laudanum` directory
	It can be prudent to remove the ASCII art and comments from the file. These items in a payload are often signatured on and can alert the defenders/AV to what you are doing

Antak - ASP.Net
	`sudo apt install nishang`
	files can be found in the `/usr/share/nishang/Antak-WebShell` directory
	remember to change the default credentials

php
	/usr/share/webshells/php/php-reverse-shell.php

bypassing content-type
in features like an image upload, often the app block us from uploading certain file types like .php.
we can try to bypass this changing the content-type from `application/x-php` to `image/gif` on our post request parameter.

resource - https://swisskyrepo.github.io/PayloadsAllTheThings/