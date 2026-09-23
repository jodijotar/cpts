basic syntax:
```
hashcat -a 0 -m 0 <hashes> [wordlist, rule, mask, ...]
```
	-a: attack mode
	-m: hash type

to see hash types ID -> `hashcat --help`

---
## mask attack
-a 3

rather than blind bruteforce, tests custom combinations of letters, number and related special char

| Symbol | Charset                              |
| ------ | ------------------------------------ |
| ?l     | abcdefghijklmnopqrstuvwxyz           |
| ?u     | ABCDEFGHIJKLMNOPQRSTUVWXYZ           |
| ?d     | 0123456789                           |
| ?h     | 0123456789abcdef                     |
| ?H     | 0123456789ABCDEF                     |
| ?s     | `«space»!"#$%&'()*+,-./:;<=>?@[]^_{` |
| ?a     | ?l?u?d?s                             |
| ?b     | 0x00 - 0xff                          |

custom charsets can be defined with the `-1`, `-2`, `-3`, and `-4` arguments, then referred to with `?1`, `?2`, `?3`, and `?4`

use example:
```
hashcat -a 3 -m 0 1e293d6912d074c0fd15844d803400dd '?u?l?l?l?l?d?s'
```

---
## rules
-r

list
```
ls -l /usr/share/hashcat/rules
```

best 66
```
-r /usr/share/hashcat/rules/best66.rule
```
this rule set generates variations of the words, such as capitalizing the first letter, appending numbers, or substituting characters

[[custom rules]]

---
