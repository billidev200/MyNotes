# FTP/21 Enumeration

## FTP modes

### 1. Active Mode (PORT Mode)

* The **client** opens a random port (>1023) and tells the server:\
  “Hey, connect back to me on this port for the data transfer.”
* Then the **server initiates the connection** from its data port (port 20) back to the client’s chosen port.

✅ Works well if the client is on an open network.\
❌ Problems if the client is behind a firewall/NAT, because the server has to _initiate a connection back_ to the client.

### 2. Passive Mode (PASV Mode)

* The **server** opens a random port (>1023) and tells the client:\
  “Hey, connect to me on this port for the data transfer.”
* Then the **client initiates the connection** to the server’s chosen port.

✅ Works better with firewalls and NAT (client always initiates connections).\
❌ Server needs to keep many ports open.

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

## Metasploit Auxiliary modules

### Most important

| Module Name                            | Description                                                |
| -------------------------------------- | ---------------------------------------------------------- |
| `auxiliary/scanner/ftp/ftp_version`    | Detect FTP server version and banner                       |
| `auxiliary/scanner/ftp/anonymous`      | Check for anonymous FTP login allowed                      |
| `auxiliary/scanner/ftp/ftp_login`      | Brute force FTP login with a user/pass list                |
| `auxiliary/scanner/ftp/ftp_login_enum` | Enumerate valid FTP usernames (user enumeration)           |
| `auxiliary/scanner/ftp/ftp_syst`       | Get FTP system info (SYST command)                         |
| `auxiliary/scanner/ftp/ftp_list`       | Enumerate directory listing if anonymous access is allowed |

### All modules

<table><thead><tr><th width="47">#</th><th width="176">Module Path</th><th>Date</th><th>Rank</th><th>Priv?</th><th>Description</th></tr></thead><tbody><tr><td>0</td><td>auxiliary/scanner/ftp/anonymous</td><td>.</td><td>normal</td><td>No</td><td>Anonymous FTP Access Detection</td></tr><tr><td>1</td><td>auxiliary/server/capture/ftp</td><td>.</td><td>normal</td><td>No</td><td>Authentication Capture: FTP</td></tr><tr><td>2</td><td>auxiliary/scanner/ftp/bison_ftp_traversal</td><td>2015-09-28</td><td>normal</td><td>Yes</td><td>BisonWare BisonFTP Server 3.5 Directory Traversal Info Disclosure</td></tr><tr><td>3</td><td>auxiliary/scanner/ssh/cerberus_sftp_enumusers</td><td>2014-05-27</td><td>normal</td><td>No</td><td>Cerberus FTP Server SFTP Username Enumeration</td></tr><tr><td>4</td><td>auxiliary/scanner/snmp/cisco_config_tftp</td><td>.</td><td>normal</td><td>No</td><td>Cisco IOS SNMP Configuration Grabber (TFTP)</td></tr><tr><td>5</td><td>auxiliary/scanner/snmp/cisco_upload_file</td><td>.</td><td>normal</td><td>No</td><td>Cisco IOS SNMP File Upload (TFTP)</td></tr><tr><td>6</td><td>_ action: Override_Config</td><td>.</td><td>.</td><td>.</td><td>Override the running config</td></tr><tr><td>7</td><td>_ action: Upload_File</td><td>.</td><td>.</td><td>.</td><td>Upload the file</td></tr><tr><td>8</td><td>auxiliary/admin/networking/cisco_vpn_3000_ftp_bypass</td><td>2006-08-23</td><td>normal</td><td>No</td><td>Cisco VPN Concentrator 3000 FTP Unauthorized Admin Access</td></tr><tr><td>9</td><td>auxiliary/scanner/ftp/colorado_ftp_traversal</td><td>2016-08-11</td><td>normal</td><td>Yes</td><td>ColoradoFTP Server 1.3 Build 8 Directory Traversal Info Disclosure</td></tr><tr><td>10</td><td>auxiliary/gather/crushftp_authbypass_cve_2025_2825</td><td>.</td><td>normal</td><td>No</td><td>CrushFTP AWS4-HMAC Authentication Bypass</td></tr><tr><td>11</td><td>auxiliary/gather/crushftp_fileread_cve_2024_4040</td><td>.</td><td>normal</td><td>Yes</td><td>CrushFTP Unauthenticated Arbitrary File Read</td></tr><tr><td>12</td><td>auxiliary/scanner/ftp/easy_file_sharing_ftp</td><td>2017-03-07</td><td>normal</td><td>Yes</td><td>Easy File Sharing FTP Server 3.6 Directory Traversal</td></tr><tr><td>13</td><td>auxiliary/scanner/ftp/ftp_login</td><td>.</td><td>normal</td><td>No</td><td>FTP Authentication Scanner</td></tr><tr><td>14</td><td>auxiliary/scanner/portscan/ftpbounce</td><td>.</td><td>normal</td><td>No</td><td>FTP Bounce Port Scanner</td></tr><tr><td>15</td><td>auxiliary/server/ftp</td><td>.</td><td>normal</td><td>No</td><td>FTP File Server</td></tr><tr><td>16</td><td>auxiliary/scanner/ftp/ftp_version</td><td>.</td><td>normal</td><td>No</td><td>FTP Version Scanner</td></tr><tr><td>17</td><td>auxiliary/dos/windows/ftp/filezilla_admin_user</td><td>2005-11-07</td><td>normal</td><td>No</td><td>FileZilla FTP Server Admin Interface Denial of Service</td></tr><tr><td>18</td><td>auxiliary/dos/windows/ftp/filezilla_server_port</td><td>2006-12-11</td><td>normal</td><td>No</td><td>FileZilla FTP Server Malformed PORT DoS</td></tr><tr><td>19</td><td>auxiliary/server/wget_symlink_file_write</td><td>2014-10-27</td><td>normal</td><td>No</td><td>GNU Wget FTP Symlink Arbitrary Filesystem Access</td></tr><tr><td>20</td><td>auxiliary/dos/scada/d20_tftp_overflow</td><td>2012-01-19</td><td>normal</td><td>No</td><td>GE D20ME TFTP Server Buffer Overflow DoS</td></tr><tr><td>21</td><td>auxiliary/dos/windows/ftp/guildftp_cwdlist</td><td>2008-10-12</td><td>normal</td><td>No</td><td>Guild FTPd 0.999.8.11/0.999.14 Heap Corruption</td></tr><tr><td>22</td><td>auxiliary/scanner/tftp/ipswitch_whatsupgold_tftp</td><td>2011-12-12</td><td>normal</td><td>No</td><td>IpSwitch WhatsUp Gold TFTP Directory Traversal</td></tr><tr><td>23</td><td>auxiliary/scanner/ftp/konica_ftp_traversal</td><td>2015-09-22</td><td>normal</td><td>Yes</td><td>Konica Minolta FTP Utility 1.00 Directory Traversal Info Disclosure</td></tr><tr><td>24</td><td>auxiliary/dos/windows/ftp/iis75_ftpd_iac_bof</td><td>2010-12-21</td><td>normal</td><td>No</td><td>Microsoft IIS FTP Server Encoded Response Overflow</td></tr><tr><td>25</td><td>auxiliary/dos/windows/ftp/iis_list_exhaustion</td><td>2009-09-03</td><td>normal</td><td>No</td><td>Microsoft IIS FTP Server LIST Stack Exhaustion</td></tr><tr><td>26</td><td>auxiliary/scanner/tftp/netdecision_tftp</td><td>2009-05-16</td><td>normal</td><td>No</td><td>NetDecision 4.2 TFTP Directory Traversal</td></tr><tr><td>27</td><td>auxiliary/scanner/ftp/pcman_ftp_traversal</td><td>2015-09-28</td><td>normal</td><td>Yes</td><td>PCMan FTP Server 2.0.7 Directory Traversal Info Disclosure</td></tr><tr><td>28</td><td>auxiliary/dos/windows/tftp/pt360_write</td><td>2008-10-29</td><td>normal</td><td>No</td><td>PacketTrap TFTP Server 2.2.5459.0 DoS</td></tr><tr><td>29</td><td>auxiliary/gather/progress_moveit_sftp_fileread_cve_2024_5806</td><td>2024-06-25</td><td>normal</td><td>Yes</td><td>Progress MOVEit SFTP Auth Bypass for Arbitrary File Read</td></tr><tr><td>30</td><td>auxiliary/fuzzers/ftp/client_ftp</td><td>.</td><td>normal</td><td>No</td><td>Simple FTP Client Fuzzer</td></tr><tr><td>31</td><td>auxiliary/fuzzers/ftp/ftp_pre_post</td><td>.</td><td>normal</td><td>No</td><td>Simple FTP Fuzzer</td></tr><tr><td>32</td><td>auxiliary/dos/windows/ftp/solarftp_user</td><td>2011-02-22</td><td>normal</td><td>No</td><td>Solar FTP Server Malformed USER DoS</td></tr><tr><td>33</td><td>auxiliary/dos/windows/tftp/solarwinds</td><td>2010-05-21</td><td>normal</td><td>No</td><td>SolarWinds TFTP Server 10.4.0.10 DoS</td></tr><tr><td>34</td><td>auxiliary/scanner/tftp/tftpbrute</td><td>.</td><td>normal</td><td>No</td><td>TFTP Brute Forcer</td></tr><tr><td>35</td><td>auxiliary/server/tftp</td><td>.</td><td>normal</td><td>No</td><td>TFTP File Server</td></tr><tr><td>36</td><td>auxiliary/admin/tftp/tftp_transfer_util</td><td>.</td><td>normal</td><td>No</td><td>TFTP File Transfer Utility</td></tr><tr><td>37</td><td>_ action: Download</td><td>.</td><td>.</td><td>.</td><td>Download REMOTE_FILENAME as FILENAME from the server</td></tr><tr><td>38</td><td>_ action: Upload</td><td>.</td><td>.</td><td>.</td><td>Upload FILENAME as REMOTE_FILENAME to the server</td></tr><tr><td>39</td><td>auxiliary/scanner/http/titan_ftp_admin_pwd</td><td>.</td><td>normal</td><td>No</td><td>Titan FTP Admin Password Disclosure</td></tr><tr><td>40</td><td>auxiliary/dos/windows/ftp/titan626_site</td><td>2008-10-14</td><td>normal</td><td>No</td><td>Titan FTP Server 6.26.630 SITE WHO DoS</td></tr><tr><td>41</td><td>auxiliary/scanner/ftp/titanftp_xcrc_traversal</td><td>2010-06-15</td><td>normal</td><td>No</td><td>Titan FTP XCRC Directory Traversal Info Disclosure</td></tr><tr><td>42</td><td>auxiliary/dos/ftp/vsftpd_232</td><td>2011-02-03</td><td>normal</td><td>Yes</td><td>VSFTPD 2.3.2 DoS</td></tr><tr><td>43</td><td>auxiliary/dos/windows/ftp/vicftps50_list</td><td>2008-10-24</td><td>normal</td><td>No</td><td>Victory FTP Server 5.0 LIST DoS</td></tr><tr><td>44</td><td>auxiliary/dos/windows/ftp/winftp230_nlst</td><td>2008-09-26</td><td>normal</td><td>No</td><td>WinFTP 2.3.0 NLST DoS</td></tr><tr><td>45</td><td>auxiliary/dos/windows/ftp/xmeasy560_nlst</td><td>2008-10-13</td><td>normal</td><td>No</td><td>XM Easy Personal FTP Server 5.6.0 NLST DoS</td></tr><tr><td>46</td><td>auxiliary/dos/windows/ftp/xmeasy570_nlst</td><td>2009-03-27</td><td>normal</td><td>No</td><td>XM Easy Personal FTP Server 5.7.0 NLST DoS</td></tr></tbody></table>
