# Networking

## wget

```bash
wget [options] <URL>
```

#### 🔸 Tips:

* Use `-q` for quiet mode (no output).
* Use `--no-check-certificate` if the SSL cert is invalid (not recommended for secure sites).

| Use Case                      | Command                                                | Explanation                           |
| ----------------------------- | ------------------------------------------------------ | ------------------------------------- |
| Download a file               | `wget https://example.com/file.zip`                    | Saves `file.zip` in current directory |
| Save with a custom name       | `wget -O newname.zip https://example.com/file.zip`     | Saves file as `newname.zip`           |
| Continue interrupted download | `wget -c https://example.com/file.zip`                 | Resumes download if interrupted       |
| Download in background        | `wget -b https://example.com/file.zip`                 | Runs download in background           |
| Limit download speed          | `wget --limit-rate=500k https://example.com/file.zip`  | Max speed: 500 KB/s                   |
| Mirror a full site            | `wget -m https://example.com`                          | Recursively downloads the entire site |
| Download recursively          | `wget -r https://example.com/folder/`                  | Downloads entire folder tree          |
| Specify user-agent            | `wget --user-agent="Mozilla" https://example.com`      | Spoofs browser identity               |
| Use authentication            | `wget --user=user --password=pass https://example.com` | For login-protected files             |

## curl

```bash
curl [options] <URL>
```

Make a JSON POST request:

```bash
curl -X POST -H "Content-Type: application/json" \
     -d '{"name": "John"}' \
     https://api.example.com/users
```

| Purpose                 | Command                                                                                         | Explanation                      |
| ----------------------- | ----------------------------------------------------------------------------------------------- | -------------------------------- |
| Download a file         | `curl -O https://example.com/file.zip`                                                          | Save file with original name     |
| Save with a custom name | `curl -o newfile.zip https://example.com/file.zip`                                              | Save file as `newfile.zip`       |
| Follow redirects        | `curl -L https://short.url`                                                                     | Follows URL redirects            |
| Get HTTP headers only   | `curl -I https://example.com`                                                                   | Shows response headers           |
| Send GET request        | `curl https://api.example.com/data`                                                             | Basic GET request                |
| Send POST request       | `curl -X POST -d "key=value" https://example.com`                                               | Submit form data                 |
| Send JSON data          | `curl -X POST -H "Content-Type: application/json" -d '{"key":"value"}' https://api.example.com` | API-style POST                   |
| Use Basic Auth          | `curl -u username:password https://example.com`                                                 | Authenticate via HTTP Basic Auth |
| Download silently       | `curl -s https://example.com`                                                                   | Suppresses progress output       |

## ping

The `ping` command has options to change how it works:

* `-c` - Send a specific number of ping requests
* `-i` - Wait a specific number of seconds between sending each packet
* `-t` - Set the IP Time to Live (TTL)
* `-q` - Quiet output, only show summary
* `-s` - Specify the number of data bytes to be sent

## ifconfig

Used to view and configure network interfaces in older Linux systems. It shows IP addresses, MAC addresses, status, etc.

## netstat(legacy)

```bash
netstat [OPTIONS]
```

| Option       | Description                                                         |
| ------------ | ------------------------------------------------------------------- |
| `-a`         | Show all sockets (listening and non-listening)                      |
| `-t`         | Show TCP connections                                                |
| `-u`         | Show UDP connections                                                |
| `-l`         | Show only listening sockets                                         |
| `-p`         | Show PID and program name for each socket (requires sudo)           |
| `-n`         | Show numerical addresses instead of resolving hostnames             |
| `-r`         | Show the routing table                                              |
| `-i`         | Show network interfaces and statistics                              |
| `-s`         | Show network statistics by protocol                                 |
| `-c`         | Continuously display output (refresh)                               |
| `-e`         | Show extended information                                           |
| `-v`         | Verbose output                                                      |
| `-W`         | Wide output (don't truncate addresses/ports)                        |
| `--protocol` | Display statistics for a specific protocol (e.g., `--tcp`, `--udp`) |

## ss

```bash
ss [OPTIONS]
```

multiple commands combined

```bash
sudo ss -tlnp
```

| Option | Description                                  |
| ------ | -------------------------------------------- |
| `-t`   | Show TCP sockets                             |
| `-u`   | Show UDP sockets                             |
| `-l`   | Show only listening sockets                  |
| `-a`   | Show all sockets (listening + non-listening) |
| `-p`   | Show process using socket (PID/program)      |
| `-n`   | Show numeric addresses (no DNS resolution)   |
| `-r`   | Show DNS names (reverse lookup)              |
| `-s`   | Show summary statistics                      |
| `-m`   | Show socket memory usage                     |
| `-o`   | Show timer information on sockets            |
| `-4`   | Display IPv4 sockets only                    |
| `-6`   | Display IPv6 sockets only                    |

## ip

```bash
ip [ OPTIONS ] OBJECT { COMMAND | help }
```

```bash
ip a
```

* **OBJECT** can be things like `addr` (addresses), `link` (network interfaces), `route`, `neighbor`, etc.
* **COMMAND** is an action like `show`, `add`, `delete`, `flush`, etc.

| Object     | Description                       | Common Commands      |
| ---------- | --------------------------------- | -------------------- |
| `link`     | Network interfaces (up/down, MAC) | `show`, `set`        |
| `addr`     | IP addresses (add, delete, show)  | `show`, `add`, `del` |
| `route`    | Routing table                     | `show`, `add`, `del` |
| `neighbor` | ARP or neighbor entries           | `show`, `add`, `del` |

## ssh

Here are some common options you can use with the `ssh` command:

* `-p` - Specify the port
* `-i` - Use a private key file, This is useful when you have a specific key for a server.
* `-v` - Enable verbose mode,which provides detailed information about the SSH connection process.
* `-C` - Enable compression
* `-X` - Enable X11 forwarding
* `-o` - Specify options directly on the command line

```bash
ssh -o StrictHostKeyChecking=no user@example.com
```

```bash
ssh user@example.com
```

```bash
ssh -p 2222 user@example.com
```

## scp

The `scp` command supports various options to customize its behavior:

* `-r` - Recursively copy entire directories
* `-P` - Specify the port to connect to on the remote host
* `-i` - Specify an identity (private key) file
* `-C` - Enable compression
* `-v` - Enable verbose mode
* `-l` - Limit the bandwidth used by the copy

```bash
scp file.txt user@example.com:/home/user/
```

## netdiscover

The `netdiscover` command is a **network reconnaissance tool** used to discover **live hosts** (devices) on a local network by performing **ARP (Address Resolution Protocol) scans**. It’s commonly used in penetration testing or network troubleshooting to quickly find IP and MAC addresses of devices connected to a subnet.

```bash
netdiscover [options]
```

| Option           | Description                                                       |
| ---------------- | ----------------------------------------------------------------- |
| `-i <interface>` | Use a specific network interface (e.g., `eth0`, `wlan0`).         |
| `-r <range>`     | Scan a specific IP range or subnet (e.g., `192.168.1.0/24`).      |
| `-p`             | Passive mode (listen only, no ARP requests sent).                 |
| `-s <time>`      | Time to sleep between each request (in microseconds).             |
| `-c <count>`     | Number of times to send ARP requests to each host.                |
| `-n`             | Do not resolve MAC addresses to vendor names.                     |
| `-f`             | Enable fast mode (send fewer packets, quicker but less accurate). |
| `-m <mac>`       | Filter results by MAC address or vendor (e.g., `00:11:22:*`).     |
| `-l`             | Enable long output format (more detailed).                        |
| `-S`             | Enable static scan mode (do not update screen in real-time).      |
| `-N`             | Do not print header (useful for scripts or logging).              |
| `-b`             | Enable beep sound on each new host found.                         |
| `-h`             | Show help message with all options.                               |

***

## Host

The `host` command is a simple DNS lookup utility available on **Linux, macOS**, and other Unix-like systems. It allows you to query **DNS records** for a domain — such as IP addresses, mail servers, name servers, etc.

| Command                    | Description                                                           |
| -------------------------- | --------------------------------------------------------------------- |
| `host example.com`         | Basic A/AAAA record lookup (IPv4/IPv6)                                |
| `host -t MX example.com`   | Shows mail exchange (MX) records                                      |
| `host -t NS example.com`   | Shows name servers (NS)                                               |
| `host -t TXT example.com`  | Shows TXT records (SPF, verification, etc.)                           |
| `host -a example.com`      | Performs an "all records" query                                       |
| `host example.com 8.8.8.8` | <p></p><p>Queries Google's public DNS (instead of system default)</p> |

## Dig

The `dig` command (short for **Domain Information Groper**) is a powerful DNS lookup tool used to **query DNS servers** and **troubleshoot domain name system issues**.

| Command      | What It Does                    | Example                     |
| ------------ | ------------------------------- | --------------------------- |
| `dig A`      | Get IPv4 address                | `dig A example.com`         |
| `dig AAAA`   | Get IPv6 address                | `dig AAAA example.com`      |
| `dig MX`     | Mail servers                    | `dig MX example.com`        |
| `dig NS`     | Name servers                    | `dig NS example.com`        |
| `dig TXT`    | Get TXT records (SPF, etc.)     | `dig TXT example.com`       |
| `dig CNAME`  | Canonical name (alias)          | `dig CNAME www.example.com` |
| `dig ANY`    | Get all available record types  | `dig ANY example.com`       |
| `dig +short` | Output only result (clean view) | `dig example.com +short`    |
