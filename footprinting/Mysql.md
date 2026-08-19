usually the service runs on port `3306`

Default Configuration
```
sudo apt install mysql-server -y
```
```
cat /etc/mysql/mysql.conf.d/mysqld.cnf | grep -v "#" | sed -r '/^\s*$/d'
```

Dangerous settings and configs --- https://dev.mysql.com/doc/refman/8.0/en/server-system-variables.html

| Settings         | Description                                                                                                  |
| ---------------- | ------------------------------------------------------------------------------------------------------------ |
| user             | Sets which user the MySQL service will run as.                                                               |
| password         | Sets the password for the MySQL user.                                                                        |
| admin_address    | The IP address on which to listen for TCP/IP connections on the administrative network interface.            |
| debug            | This variable indicates the current debugging settings                                                       |
| sql_warnings     | This variable controls whether single-row INSERT statements produce an information string if warnings occur. |
| secure_file_priv | This variable is used to limit the effect of data import and export operations.                              |

SQL commands ---

| Command                                              | Description                                        |
| ---------------------------------------------------- | -------------------------------------------------- |
| `mysql -u <user> -p<password> -h <IP address>`       | connect to mysql server                            |
| `show databases;`                                    | show all databases                                 |
| `use <database>;`                                    | select one of the existing databases               |
| `show tables;`                                       | show all available tables in the selected database |
| `show columns from <table>;`                         | show all columns in the selected table             |
| `select * from <table>; `                            | show everything in the desired table               |
| `select * from <table> where <column> = "<string>";` | search for needed string in the desired table      |

Footprinting
```
sudo nmap <ip> -sV -sC -p3306 --script mysql*
```

shell to mysql server
```
mysql -u root -h <ip>
```

security issues resource
	https://dev.mysql.com/doc/refman/8.0/en/general-security-issues.html