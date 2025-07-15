# MySQL/3306 Enumeration

## Nmap scripts

**Show nmap MySQL scripts**

```bash
ls -al /usr/share/nmap/scripts/ | grep -e "mysql"
```

**Open MySQL from web**

```bash
mysql://$ipaddress 
```

**MySQL script run example**

Attempts to brute-force MySQL logins using a wordlist.

```bash
nmap -p {MySQL PORT} --script mysql-brute <target>
```

**Use Multiple scripts**

```bash
nmap -p {MySQL PORT} --script mysql-brute,mysql-enum <target>
```

#### All scripts

| Script Name                 | Description                                                           |
| --------------------------- | --------------------------------------------------------------------- |
| mysql-audit.nse             | Runs an audit of MySQL security settings and configuration.           |
| mysql-brute.nse             | Attempts to brute-force MySQL logins using a wordlist.                |
| mysql-databases.nse         | Enumerates available MySQL databases.                                 |
| mysql-dump-hashes.nse       | Extracts MySQL password hashes for offline cracking.                  |
| mysql-empty-password.nse    | Checks if any MySQL accounts have empty passwords.                    |
| mysql-enum.nse              | Performs MySQL enumeration, listing users, databases, and privileges. |
| mysql-info.nse              | Retrieves general information about the MySQL server.                 |
| mysql-query.nse             | Runs custom SQL queries on the target MySQL database.                 |
| mysql-users.nse             | Enumerates MySQL user accounts.                                       |
| mysql-variables.nse         | Lists MySQL system variables and settings.                            |
| mysql-vuln-cve2012-2122.nse | Checks for MySQL authentication bypass vulnerability (CVE-2012-2122). |

## Metasploit Auxiliary

<figure><img src="../../../../../.gitbook/assets/image (2) (1) (1).png" alt=""><figcaption></figcaption></figure>
