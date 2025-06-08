# Networking

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

## curl

## wget

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

