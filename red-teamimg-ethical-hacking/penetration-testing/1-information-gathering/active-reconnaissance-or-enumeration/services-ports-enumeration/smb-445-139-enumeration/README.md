# SMB/445/139 Enumeration

{% hint style="warning" %}
With smb i can login to user or kogin to folders/shares using users
{% endhint %}

{% stepper %}
{% step %}
### Enumeration

Locate users,shares with enum4linux or other
{% endstep %}

{% step %}
### Password Policy List

enum4linux -P
{% endstep %}

{% step %}
### Login

Try login to users or shares wtith smbclint or smbmap to check if you cant with no pass
{% endstep %}

{% step %}
### Brutefore

Bruteforce login user with metasploit smb\_login and then we can select share to view

or if we have password of user then we can login to shares with smbclint or smbmap
{% endstep %}
{% endstepper %}

## Enum4linux

```
enum4linux -a
```

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

## Metasploit Auxiliary

### Most imporant

| Module Name                  | Purpose                                  | Key Options                               | Example Usage Command                                                 |
| ---------------------------- | ---------------------------------------- | ----------------------------------------- | --------------------------------------------------------------------- |
| `scanner/smb/smb_version`    | Identify SMB version and OS info         | `RHOSTS`, `THREADS`                       | `use auxiliary/scanner/smb/smb_versionset RHOSTS 192.168.1.100run`    |
| `scanner/smb/smb_enumshares` | Enumerate SMB shares                     | `RHOSTS`, `THREADS`, `SMBUser`, `SMBPass` | `use auxiliary/scanner/smb/smb_enumsharesset RHOSTS 192.168.1.100run` |
| `scanner/smb/smb_enumusers`  | Enumerate SMB users (if allowed)         | `RHOSTS`, `THREADS`, `SMBUser`, `SMBPass` | `use auxiliary/scanner/smb/smb_enumusersset RHOSTS 192.168.1.100run`  |
| `scanner/smb/smb_login`      | Check SMB login credentials/null session | `RHOSTS`, `SMBUser`, `SMBPass`            | `use auxiliary/scanner/smb/smb_loginset RHOSTS 192.168.1.100run`      |

### All modules

<table><thead><tr><th width="69">#</th><th>Module Path</th><th>Date</th><th>Rank</th><th>Priv</th><th>Description</th></tr></thead><tbody><tr><td>0</td><td>auxiliary/server/capture/smb</td><td>.</td><td>normal</td><td>No</td><td>Authentication Capture: SMB</td></tr><tr><td>1</td><td>auxiliary/server/relay/esc8</td><td>.</td><td>normal</td><td>Yes</td><td>ESC8 Relay: SMB to HTTP(S)</td></tr><tr><td>2</td><td>auxiliary/admin/smb/ms17_010_command</td><td>2017-03-14</td><td>normal</td><td>No</td><td>MS17-010 EternalRomance/EternalSynergy/EternalChampion SMB RCE</td></tr><tr><td>7</td><td>auxiliary/scanner/smb/smb_ms17_010</td><td>.</td><td>normal</td><td>No</td><td>MS17-010 SMB RCE Detection</td></tr><tr><td>10</td><td>auxiliary/dos/windows/smb/ms09_050_smb2_negotiate_pidhigh</td><td>.</td><td>normal</td><td>No</td><td>Microsoft SRV2.SYS SMB Negotiate PID Function Table Dereference</td></tr><tr><td>11</td><td>auxiliary/dos/windows/smb/ms09_050_smb2_session_logoff</td><td>.</td><td>normal</td><td>No</td><td>Microsoft SRV2.SYS SMB2 Logoff Remote Kernel NULL Pointer Dereference</td></tr><tr><td>12</td><td>auxiliary/dos/windows/smb/vista_negotiate_stop</td><td>.</td><td>normal</td><td>No</td><td>Microsoft Vista SP0 SMB Negotiate Protocol DoS</td></tr><tr><td>13</td><td>auxiliary/dos/windows/smb/ms10_006_negotiate_response_loop</td><td>.</td><td>normal</td><td>No</td><td>Microsoft Win 7 / Server 2008 R2 SMB Client Infinite Loop</td></tr><tr><td>14</td><td>auxiliary/server/relay/smb_to_ldap</td><td>.</td><td>normal</td><td>No</td><td>Microsoft Windows SMB to LDAP Relay</td></tr><tr><td>15</td><td>auxiliary/dos/windows/smb/ms10_054_queryfs_pool_overflow</td><td>.</td><td>normal</td><td>No</td><td>Microsoft SRV.SYS SrvSmbQueryFsInformation Pool Overflow DoS</td></tr><tr><td>16</td><td>auxiliary/admin/oracle/ora_ntlm_stealer</td><td>2009-04-07</td><td>normal</td><td>No</td><td>Oracle SMB Relay Code Execution</td></tr><tr><td>17</td><td>auxiliary/scanner/sap/sap_smb_relay</td><td>.</td><td>normal</td><td>No</td><td>SAP SMB Relay Abuse</td></tr><tr><td>18</td><td>auxiliary/fuzzers/smb/smb_create_pipe_corrupt</td><td>.</td><td>normal</td><td>No</td><td>SMB Create Pipe Request Corruption</td></tr><tr><td>19</td><td>auxiliary/fuzzers/smb/smb_create_pipe</td><td>.</td><td>normal</td><td>No</td><td>SMB Create Pipe Request Fuzzer</td></tr><tr><td>20</td><td>auxiliary/admin/smb/list_directory</td><td>.</td><td>normal</td><td>No</td><td>SMB Directory Listing Utility</td></tr><tr><td>21</td><td>auxiliary/scanner/smb/smb_enumusers_domain</td><td>.</td><td>normal</td><td>No</td><td>SMB Domain User Enumeration</td></tr><tr><td>22</td><td>auxiliary/admin/smb/delete_file</td><td>.</td><td>normal</td><td>No</td><td>SMB File Delete Utility</td></tr><tr><td>23</td><td>auxiliary/admin/smb/download_file</td><td>.</td><td>normal</td><td>No</td><td>SMB File Download Utility</td></tr><tr><td>24</td><td>auxiliary/admin/smb/upload_file</td><td>.</td><td>normal</td><td>No</td><td>SMB File Upload Utility</td></tr><tr><td>25</td><td>auxiliary/scanner/smb/smb_enum_gpp</td><td>.</td><td>normal</td><td>No</td><td>SMB Group Policy Preference Passwords Enumeration</td></tr><tr><td>26</td><td>auxiliary/scanner/smb/smb_login</td><td>.</td><td>normal</td><td>No</td><td>SMB Login Check Scanner</td></tr><tr><td>27</td><td>auxiliary/fuzzers/smb/smb_ntlm1_login_corrupt</td><td>.</td><td>normal</td><td>No</td><td>SMB NTLMv1 Login Request Corruption</td></tr><tr><td>28</td><td>auxiliary/fuzzers/smb/smb_negotiate_corrupt</td><td>.</td><td>normal</td><td>No</td><td>SMB Negotiate Dialect Corruption</td></tr><tr><td>29</td><td>auxiliary/fuzzers/smb/smb2_negotiate_corrupt</td><td>.</td><td>normal</td><td>No</td><td>SMB Negotiate SMB2 Dialect Corruption</td></tr><tr><td>30</td><td>auxiliary/admin/smb/change_password</td><td>.</td><td>normal</td><td>No</td><td>SMB Password Change</td></tr><tr><td>34</td><td>_ action: RESET_NTLM</td><td>.</td><td>.</td><td>.</td><td>andard reset.</td></tr><tr><td>35</td><td>auxiliary/scanner/smb/smb_lookupsid</td><td>.</td><td>normal</td><td>No</td><td>SMB SID User Enumeration (LookupSid)</td></tr><tr><td>36</td><td>_ action: DOMAIN</td><td>.</td><td>.</td><td>.</td><td>Enumerate domain accounts</td></tr><tr><td>37</td><td>_ action: LOCAL</td><td>.</td><td>.</td><td>.</td><td>Enumerate local accounts</td></tr><tr><td>38</td><td>auxiliary/admin/smb/check_dir_file</td><td>.</td><td>normal</td><td>No</td><td>SMB Scanner Check File/Directory Utility</td></tr><tr><td>39</td><td>auxiliary/scanner/smb/pipe_auditor</td><td>.</td><td>normal</td><td>No</td><td>SMB Session Pipe Auditor</td></tr><tr><td>40</td><td>auxiliary/scanner/smb/pipe_dcerpc_auditor</td><td>.</td><td>normal</td><td>No</td><td>SMB Session Pipe DCERPC Auditor</td></tr><tr><td>41</td><td>auxiliary/scanner/smb/smb_enumshares</td><td>.</td><td>normal</td><td>No</td><td>SMB Share Enumeration</td></tr><tr><td>42</td><td>auxiliary/fuzzers/smb/smb_tree_connect_corrupt</td><td>.</td><td>normal</td><td>No</td><td>SMB Tree Connect Request Corruption</td></tr><tr><td>43</td><td>auxiliary/fuzzers/smb/smb_tree_connect</td><td>.</td><td>normal</td><td>No</td><td>SMB Tree Connect Request Fuzzer</td></tr><tr><td>44</td><td>auxiliary/scanner/smb/smb_enumusers</td><td>.</td><td>normal</td><td>No</td><td>SMB User Enumeration (SAM EnumUsers)</td></tr><tr><td>45</td><td>auxiliary/scanner/smb/smb_version</td><td>.</td><td>normal</td><td>No</td><td>SMB Version Detection</td></tr><tr><td>46</td><td>auxiliary/server/relay/relay_get_naa_credentials</td><td>.</td><td>normal</td><td>Yes</td><td>SMB to HTTP relay version of Get NAA Creds</td></tr><tr><td>47</td><td>auxiliary/dos/smb/smb_loris</td><td>2017-06-29</td><td>normal</td><td>No</td><td>SMBLoris NBSS Denial of Service</td></tr><tr><td>48</td><td>auxiliary/scanner/snmp/snmp_enumshares</td><td>.</td><td>normal</td><td>No</td><td>SNMP Windows SMB Share Enumeration</td></tr><tr><td>49</td><td>auxiliary/server/teamviewer_uri_smb_redirect</td><td>.</td><td>normal</td><td>No</td><td>TeamViewer Unquoted URI Handler SMB Redirect</td></tr><tr><td>50</td><td>auxiliary/fileformat/multidrop</td><td>.</td><td>normal</td><td>No</td><td>Windows SMB Multi Dropper</td></tr></tbody></table>
