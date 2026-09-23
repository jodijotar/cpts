related notes:
	[[rules by OSINT]]

doc: https://hashcat.net/wiki/doku.php?id=rule_based_attack

| **Function** | **Description**                                  |
| ------------ | ------------------------------------------------ |
| `:`          | Do nothing                                       |
| `l`          | Lowercase all letters                            |
| `u`          | Uppercase all letters                            |
| `c`          | Capitalize the first letter and lowercase others |
| `sXY`        | Replace all instances of X with Y                |
| `$!`         | Add the exclamation character at the end         |

example:
```
cat custom.rule

:
c
so0
c so0
sa@
c sa@
c sa@ so0
$!
$! c
$! so0
$! sa@
$! c so0
$! c sa@
$! so0 sa@
$! c so0 sa@
```

check the mutated results by the rule
```
hashcat --force password.list -r custom.rule --stdout | sort -u > mut_password.list
```