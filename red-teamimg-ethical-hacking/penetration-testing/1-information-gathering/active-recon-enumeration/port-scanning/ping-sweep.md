---
description: >-
  A ping sweep is used to identify which hosts (devices) are alive or responsive
  on a network.
---

# Ping sweep

#### 🧭 **Main Uses of Ping Sweep:**

**1. ✅ Host Discovery**

* Quickly find **active devices** on a network.
* Used before more detailed scans (like port scans).

**2. 🧪 Network Mapping**

* Helps map out the devices within a **subnet or IP range**.
* Common first step in reconnaissance or network inventory.

**3. 🔐 Penetration Testing & Ethical Hacking**

* Identify live targets for further scanning (e.g., port scanning, vulnerability scanning).
* Often the **first phase of active recon**.

**4. 🛠️ System & Network Administration**

* Check if a group of systems (servers, routers, IoT devices) are up and reachable.
* Useful for **automated monitoring scripts**.

**5. ⚠️ Security Auditing**

* Detect unauthorized or rogue devices connected to the network.

## fping

### ✅ **Basic Syntax**

```bash
fping [options] [hosts or IPs]
```

You can specify:

* A single host or IP: `fping 192.168.1.1`
* Multiple hosts: `fping host1 host2`
* From a file: `fping < hostlist.txt`

### 🔹 **Commonly Used Options**

| Option | Description                                                        |
| ------ | ------------------------------------------------------------------ |
| `-a`   | Show **alive** hosts only                                          |
| `-u`   | Show **unreachable** hosts only                                    |
| `-g`   | Generate IP range or subnet (e.g., `-g 192.168.1.1 192.168.1.254`) |
| `-r N` | Retry count (how many times to retry unanswered pings)             |
| `-c N` | Number of pings per host                                           |
| `-t N` | Timeout in milliseconds                                            |
| `-q`   | Quiet output (summary only)                                        |
| `-e`   | Show elapsed time for each host                                    |
| `-s`   | Print per-host summary statistics                                  |
| `-i N` | Interval between sending pings to each host (ms)                   |
| `-p N` | Interval between ping packets to the same host (ms)                |
| `-f`   | Read list of hosts from a file (e.g., `fping -f hosts.txt`)        |

### 🧪 **Advanced Options**

| Option      | Description                    |
| ----------- | ------------------------------ |
| `-b N`      | Set socket buffer size         |
| `-B N`      | Set exponential backoff factor |
| `-H`        | Print hostnames instead of IPs |
| `-n`        | Print IPs instead of hostnames |
| `-d`        | Use DNS reverse lookup         |
| `-h`        | Show help message              |
| `--version` | Display version info           |

### 🧾 **Examples**

🔍 Ping sweep of a /24 subnet and show alive hosts only:

```bash
fping -a -g 192.168.1.0/24
```

🧪 Send 5 pings per host with 500ms timeout:

```bash
fping -c 5 -t 500 192.168.1.1 192.168.1.2
```

📄 Ping hosts listed from a file:

```bash
fping -f hosts.txt
```

🔕 Quiet mode, good for scripting:

```bash
fping -aqg 10.0.0.0/24
```

## Nmap

### 🔹 **Host Discovery (Ping Sweep)**

| Command                      | Description                                             |
| ---------------------------- | ------------------------------------------------------- |
| `nmap -sn 192.168.1.0/24`    | Ping sweep – discovers live hosts without port scanning |
| `nmap -PE -sn [range]`       | ICMP Echo Request (classic ping)                        |
| `nmap -PP -sn [range]`       | ICMP Timestamp Request                                  |
| `nmap -PS80,443 -sn [range]` | TCP SYN ping to ports 80/443                            |
| `nmap -PU53 -sn [range]`     | UDP ping to port 53 (useful for systems blocking ICMP)  |
