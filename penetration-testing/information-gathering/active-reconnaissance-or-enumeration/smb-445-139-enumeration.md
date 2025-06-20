# SMB/445/139 Enumeration

## Nmap scripts

**Show nmap SMB scripts**

```bash
ls -al /usr/share/nmap/scripts/ | grep -e "smb"
```

**SMB script run example**

Checks for SMB-related vulnerabilities (e.g., MS08-067, MS17-010).

```bash
nmap -p {SMB PORT} --script smb-check-vulns <target>
```

**Use Multiple scripts**

```bash
nmap -p {SMB PORT} --script smb-check-vulns,smb-ls <target>
```

#### All scripts

| **Script Name**            | **Description**                                                             | **Usage Example**                                                                  |
| -------------------------- | --------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- |
| **smb-os-discovery**       | Discovers OS, hostname, domain, and workgroup via SMB.                      | `nmap --script smb-os-discovery -p445 <target>`                                    |
| **smb-enum-shares**        | Lists SMB shares (including hidden ones) and permissions.                   | `nmap --script smb-enum-shares -p445 <target>`                                     |
| **smb-enum-users**         | Enumerates users on the system via SMB (requires valid credentials).        | `nmap --script smb-enum-users -p445 <target>`                                      |
| **smb-enum-groups**        | Lists local groups on the SMB server.                                       | `nmap --script smb-enum-groups -p445 <target>`                                     |
| **smb-enum-sessions**      | Retrieves active sessions on the SMB server.                                | `nmap --script smb-enum-sessions -p445 <target>`                                   |
| **smb-enum-domains**       | Enumerates available domains on a Windows network.                          | `nmap --script smb-enum-domains -p445 <target>`                                    |
| **smb-enum-services**      | Lists services running on the remote SMB server.                            | `nmap --script smb-enum-services -p445 <target>`                                   |
| **smb-enum-processes**     | Retrieves running processes from the remote system (requires admin rights). | `nmap --script smb-enum-processes -p445 <target>`                                  |
| **smb-system-info**        | Gathers detailed system information (OS, architecture, uptime).             | `nmap --script smb-system-info -p445 <target>`                                     |
| **smb-protocols**          | Lists supported SMB protocols (SMBv1, SMBv2, SMBv3).                        | `nmap --script smb-protocols -p445 <target>`                                       |
| **smb-security-mode**      | Reports SMB security settings (signing, encryption).                        | `nmap --script smb-security-mode -p445 <target>`                                   |
| **smb-server-stats**       | Retrieves SMB server statistics (requires authentication).                  | `nmap --script smb-server-stats -p445 <target>`                                    |
| **smb-ls**                 | Lists files in an SMB share (requires credentials).                         | `nmap --script smb-ls --script-args smbuser=user,smbpass=pass -p445 <target>`      |
| **smb-mbenum**             | Queries the remote system's Master Browser service for network info.        | `nmap --script smb-mbenum -p445 <target>`                                          |
| **smb-vuln-ms17-010**      | Checks if the target is vulnerable to EternalBlue (MS17-010).               | `nmap --script smb-vuln-ms17-010 -p445 <target>`                                   |
| **smb-vuln-ms08-067**      | Checks for MS08-067 vulnerability (unpatched Windows systems).              | `nmap --script smb-vuln-ms08-067 -p445 <target>`                                   |
| **smb-vuln-cve2009-3103**  | Checks for buffer overflow vulnerability (CVE-2009-3103).                   | `nmap --script smb-vuln-cve2009-3103 -p445 <target>`                               |
| **smb-vuln-conficker**     | Detects Conficker worm infection.                                           | `nmap --script smb-vuln-conficker -p445 <target>`                                  |
| **smb-vuln-cve-2017-7494** | Checks for SambaCry (CVE-2017-7494) vulnerability.                          | `nmap --script smb-vuln-cve-2017-7494 -p445 <target>`                              |
| **smb2-vuln-uptime**       | Estimates system uptime via SMB2 (helps detect reboots after patching).     | `nmap --script smb2-vuln-uptime -p445 <target>`                                    |
| **smb2-security-mode**     | Reports SMB2-specific security settings.                                    | `nmap --script smb2-security-mode -p445 <target>`                                  |
| **smb-brute**              | Performs brute-force attacks against SMB passwords.                         | `nmap --script smb-brute -p445 <target>`                                           |
| **smb-ntlm-info**          | Retrieves NTLM authentication info (OS version, domain, etc.).              | `nmap --script smb-ntlm-info -p445 <target>`                                       |
| **smb-psexec**             | Runs commands remotely via PsExec (requires admin credentials).             | `nmap --script smb-psexec --script-args smbuser=admin,smbpass=pass -p445 <target>` |

| **smb-ntlm-info** | Retrieves NTLM authentication info (OS version, domain, etc.). | `nmap --script smb-ntlm-info -p445 <target>` |
| ----------------- | -------------------------------------------------------------- | -------------------------------------------- |

***

## SmbClient

is a command-line tool for accessing shared folders on SMB/CIFS networks, often used in Linux/Unix systems to interact with Windows-based file sharing.

**Connecting to a Share**

```bash
smbclient -L //hostname/sharename -U username 
```

```bash
smbclient -L $IPADDRESS
```

```bash
smbclient //hostname -U username
```

* `hostname` OR `IPaddress`is the name of the machine hosting the share.
* `sharename` is the name of the shared folder.
* `username` is the user account name.

**List the shared resource**

```bash
smbclient -L //$IPADDRESS/
```

```bash
smbclient -L $IPADDRESS
```

```bash
smbclient -L $Hostname
```

**Uploading a File**

```bash
smbclient //192.168.1.100/sharedfolder -U user
smb: \> put localfile.txt
```

**Downloading a File**

```bash
smbclient //192.168.1.100/sharedfolder -U user
smb: \> get remotefile.txt
```

The “-a” flag ( — authentication-file) is the flag used to specify the file that holds the user-password information to establish a connection. The format of the file to be specified should be as follows.

“-B” flag ( — browse): This flag uses DNS to find SMB servers.

The “-p” flag ( — port) is used to select the port to which the connection is to be made. If this flag is not used, the default port is port 139.

The “-I” flag ( — IP-address IP-address) is used to give the IP address of the server, not the NetBIOS name, for the connection.

Flag( — — kerberos): Used to try to authenticate with Kerberos.

Flag ( — debuglevel) is a flag that provides more detailed information to log files. a value of 0–10 can be given.

#### `smbclient` Commands

| Command                      | Description                                                                         |
| ---------------------------- | ----------------------------------------------------------------------------------- |
| `help` or `?`                | Shows a list of all available commands and their descriptions.                      |
| `ls`                         | List files and directories in the current directory.                                |
| `cd <directory>`             | Change the current directory to `<directory>`.                                      |
| `pwd`                        | Show the current directory on the SMB share.                                        |
| `get <remote_file>`          | Download the file `<remote_file>` from the SMB share.                               |
| `put <local_file>`           | Upload the file `<local_file>` to the SMB share.                                    |
| `mget <pattern>`             | Download multiple files matching the pattern (e.g., `*.txt`).                       |
| `mput <pattern>`             | Upload multiple files matching the pattern (e.g., `*.txt`).                         |
| `rename <oldname> <newname>` | Rename a file or directory from `<oldname>` to `<newname>`.                         |
| `del <filename>`             | Delete the file `<filename>` on the SMB share.                                      |
| `rmdir <directory>`          | Remove an empty directory `<directory>` from the share.                             |
| `mkdir <directory>`          | Create a new directory `<directory>` on the SMB share.                              |
| `exit` or `quit`             | Exit the `smbclient` interactive session.                                           |
| `reconnect`                  | Reconnect to the current share if the session was lost.                             |
| `close`                      | Close the current SMB connection but remain in `smbclient`.                         |
| `setmode <mode>`             | Set the file transfer mode (binary or ascii).                                       |
| `binary`                     | Set the transfer mode to binary (default for files).                                |
| `ascii`                      | Set the transfer mode to ASCII (useful for text files).                             |
| `status`                     | Display the current status of the connection (e.g., share name, current directory). |
| `prompt`                     | Toggle interactive prompts for multiple file transfers.                             |
| `lcd <path>`                 | Change the local working directory to `<path>`.                                     |
| `hash`                       | Enable or disable progress hash printing for large file transfers.                  |
| `version`                    | Display the SMB protocol version being used.                                        |
| `tree`                       | Display a tree view of the shared folder's contents.                                |
| `help <command>`             | Display detailed help for a specific command.                                       |
| `exit`                       | Exit the `smbclient` interactive mode.                                              |

***

## SmbMap

Basic command

```bash
smbmap -H <target_ip>
```

`-H <target_ip>` → Specifies the target machine’s IP address.

#### **Common `smbmap` Commands & Options**

| Command / Option                                                          | Description                                                |
| ------------------------------------------------------------------------- | ---------------------------------------------------------- |
| `smbmap -H <IP>`                                                          | Lists all available SMB shares on the target host.         |
| `smbmap -H <IP> -u <user>`                                                | Connects using a specific username (default is anonymous). |
| `smbmap -H <IP> -u <user> -p <password>`                                  | Uses a specific username and password for authentication.  |
| `smbmap -H <IP> -d <domain>`                                              | Specifies a domain for authentication.                     |
| `smbmap -H <IP> -u <user> -p <password> -L`                               | Lists all accessible shares and their permissions.         |
| `smbmap -H <IP> -u <user> -p <password> -r <share>`                       | Recursively lists all files in the specified share.        |
| `smbmap -H <IP> -u <user> -p <password> -R <share>`                       | Recursively lists all files, including hidden files.       |
| `smbmap -H <IP> -u <user> -p <password> -r <share> -A <pattern>`          | Searches for a specific file pattern (e.g., `*.txt`).      |
| `smbmap -H <IP> -u <user> -p <password> -x "<command>"`                   | Executes a system command via SMB (if permissions allow).  |
| `smbmap -H <IP> -u <user> -p <password> -d <domain> --shares`             | Lists available shares using domain authentication.        |
| `smbmap -H <IP> -u <user> -p <password> -w`                               | Attempts to access shares using null authentication.       |
| `smbmap -H <IP> -u <user> -p <password> -q`                               | Quiet mode (minimal output).                               |
| `smbmap -H <IP> -u <user> -p <password> --upload <local_file> -r <share>` | Uploads a file to the specified SMB share.                 |
| `smbmap -H <IP> -u <user> -p <password> --download <remote_file>`         | Downloads a file from an SMB share.                        |
