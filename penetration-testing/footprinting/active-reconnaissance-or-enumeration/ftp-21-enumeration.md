# FTP/21 Enumeration

## Nmap scripts

**Show nmap ftp scripts**

```bash
ls -al /usr/share/nmap/scripts/ | grep -e "ftp"
```

**Open ftp from web**

```bash
ftp://$ipaddress 
```

**FTP script run example**

Checks for anonymous login

```bash
nmap -p {FTP PORT} --script ftp-anon <target>
```

**Use Multiple scripts**

```bash
nmap -p {FTP PORT} --script ftp-anon,ftp-anon <target>
```

#### All scripts

| Script Name                   | Description                                                               |
| ----------------------------- | ------------------------------------------------------------------------- |
| **ftp-anon.nse**              | Checks if anonymous FTP login is allowed.                                 |
| **ftp-brute.nse**             | Performs brute-force attacks on FTP accounts.                             |
| **ftp-bounce.nse**            | Detects if an FTP server is vulnerable to the "FTP Bounce" attack.        |
| **ftp-libopie.nse**           | Detects FTP servers that support OPIE (One-time Passwords in Everything). |
| **ftp-proftpd-backdoor.nse**  | Detects backdoors in ProFTPD servers.                                     |
| **ftp-syst.nse**              | Retrieves system information using the `SYST` command.                    |
| **ftp-vsftpd-backdoor.nse**   | Checks for the VSFTPD v2.3.4 backdoor vulnerability.                      |
| **ftp-capabilities.nse**      | Lists the capabilities of an FTP server.                                  |
| **ftp-auth-ssl.nse**          | Checks if an FTP server supports SSL/TLS authentication.                  |
| **ftp-enum.nse**              | **Enumerates FTP users.**                                                 |
| **ftp-version.nse**           | **Detects the FTP server version.**                                       |
| **ftp-vuln-cve2010-4221.nse** | **Checks for CVE-2010-4221 vulnerability in certain FTP servers.**        |

