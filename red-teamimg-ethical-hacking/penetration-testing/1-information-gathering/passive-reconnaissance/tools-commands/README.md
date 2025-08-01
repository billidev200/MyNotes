---
description: Tools used for passive reconnaissance
---

# Tools - Commands

## Whois

Finds out who owns a website and provides details like contact info and registration dates.

```
whois google.com
```

***

## WhatWeb

Checks what technologies a website is using, like its content management system (CMS) or web server.

```
whatweb example.com
```

<details>

<summary>Commands</summary>

Scanning Multiple Targets From a file

```bash
whatweb -i targets.txt
```

From a list of URLs

```bash
whatweb example.com site2.com site3.com
```

Get More Details (Verbose Output)

```bash
whatweb -v <target>
```

User-Agent Spoofing

```bash
whatweb -U "Mozilla/5.0 (Windows NT 10.0; Win64; x64)" <target>
```

Using a Proxy

```bash
whatweb --proxy 127.0.0.1:8080 <target>
```

Aggressive Scan

```bash
whatweb -a 3 <target>
```

Aggression levels:

* `-a 1`: Passive (default)
* `-a 2`: Semi-aggressive
* `-a 3`: Aggressive
* `-a 4`: Heavy, may be intrusive



</details>

{% embed url="https://whatweb.net/" %}

***

## Nslookup

Looks up the IP address for a domain name or finds the domain name for an IP address.

```bash
nslookup example.com
```

By default, [`nslookup` ](#user-content-fn-1)[^1][uses ](#user-content-fn-1)[^1]port **53**, but you can specify a different one:

<pre class="language-bash"><code class="lang-bash"><strong>nslookup -port=5353 example.com
</strong></code></pre>

<details>

<summary>Querying specific DNS record types</summary>

A Record (IPv4 Address

```bash
nslookup -type=A example.com
```

AAAA Record (IPv6 Address)

```bash
nslookup -type=AAAA example.com
```

MX Record (Mail Exchange Servers)

```bash
nslookup -type=MX example.com
```

NS Record (Name Servers)

```bash
nslookup -type=NS example.com
```

TXT Record (Text Records, e.g., SPF, DKIM, DMARC)

```bash
nslookup -type=TXT example.com
```

CNAME Record (Canonical Name, alias records)

```bash
nslookup -type=CNAME sub.example.com
```

SOA Record (Start of Authority)

```bash
nslookup -type=SOA example.com
```

PTR Record (Reverse Lookup - IP to Domain):

```bash
nslookup -type=PTR 8.8.8.8
```

ANY Record (Fetches All Available DNS Records):

```bash
nslookup -type=ANY example.com
```

</details>

***

## Theharvester

Collects information like email addresses and domain names from publicly available sources for reconnaissance.

**Basic Command Structure**

```bash
theharvester -d <domain> -b <source>
```

#### **Commonly Used Options**

* **`-d <domain>`**: The target domain you are searching for information on.
* **`-b <source>`**: The data source you want to use (e.g., `google`, `bing`, `twitter`, `yahoo`, etc.).
* **`-l <limit>`**: Limit the number of results from the source.
  * Example: `-l 100` will fetch 100 results.
* **`-p`**: Perform a port scan of the target.
* **`-S`**: Search for subdomains.
* **`-t`**: Specify the type of output (e.g., `html`, `csv`).
* **`-f`**: Use a specific file for the results.
* **`-v`**: Enable verbose output for more detailed results.
* **`-n`**: Perform a DNS-based query.

#### **3. Using Specific Sources**

Some popular sources include:

* **`google`**: Google search engine.
* **`bing`**: Bing search engine.
* **`baidu`**: Baidu search engine (Chinese).
* **`yahoo`**: Yahoo search engine.
* **`twitter`**: Twitter API.
* **`linkedin`**: LinkedIn profiles.
* **`facebook`**: Facebook API.
* **`pgp`**: PGP keyservers (search for email PGP keys).

***

## Host

The `host` command is a simple DNS lookup utility available on **Linux, macOS**, and other Unix-like systems. It allows you to query/search **DNS records** for a domain — such as IP addresses, mail servers, name servers, etc.

| Command                    | Description                                                           |
| -------------------------- | --------------------------------------------------------------------- |
| `host example.com`         | Basic A/AAAA record lookup (IPv4/IPv6)                                |
| `host -t MX example.com`   | Shows mail exchange (MX) records                                      |
| `host -t NS example.com`   | Shows name servers (NS)                                               |
| `host -t TXT example.com`  | Shows TXT records (SPF, verification, etc.)                           |
| `host -a example.com`      | Performs an "all records" query                                       |
| `host example.com 8.8.8.8` | <p></p><p>Queries Google's public DNS (instead of system default)</p> |

## dnsrecon

**`dnsrecon`** is a Python-based tool designed to **enumerate DNS records** and **perform DNS reconnaissance** on a target domain. It's often included in penetration testing distributions like Kali Linux and is used to gather critical information about a domain and its infrastructure.

```bash
dnsrecon -d example.com
```

### 🧠 **What You Can Get from `dnsrecon`**

#### 1. **Standard DNS Records**

* **A records** – Maps hostnames to IP addresses.
* **AAAA records** – IPv6 address mappings.
* **MX records** – Mail servers for the domain.
* **NS records** – Nameservers for the domain.
* **CNAME records** – Canonical names or aliases.
* **SOA record** – Start of Authority info: admin email, serial, refresh times, etc.
* **TXT records** – Includes SPF, verification, or other arbitrary text.

#### 2. **Zone Transfer Data (AXFR)**

* If **misconfigured**, `dnsrecon` can perform a **zone transfer** and dump all DNS records from a nameserver — this can expose **every subdomain, IP, service, and internal host**.

| Option | Description                                                                          | Example                   |
| ------ | ------------------------------------------------------------------------------------ | ------------------------- |
| `-d`   | Target domain                                                                        | `-d example.com`          |
| `-t`   | Enumeration type(s)                                                                  | `-t std` or `-t axfr,brt` |
| `-D`   | Subdomain wordlist                                                                   | `-D wordlist.txt`         |
| `-a`   | Perform all standard tests (`std`, `ns`, `mx`, `soa`, `axfr`, `srv`, `txt`, `snoop`) | `-d example.com -a`       |
| `-r`   | Reverse lookup on CIDR or IP range                                                   | `-r 192.168.1.0/24`       |
| `-n`   | Specify name server                                                                  | `-n 8.8.8.8`              |
| `-s`   | Perform zone walk (if DNSSEC NSEC records are available)                             | `-d example.com -s`       |
| `-z`   | Enable verbose mode                                                                  | `-z`                      |
| `-j`   | Output in JSON format                                                                | `-j output.json`          |
| `-w`   | Save web-based lookup data to file                                                   | `-w whois.txt`            |

## Sublist3r

<figure><img src="../../../../../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt="" width="509"><figcaption></figcaption></figure>

**Sublist3r** finds subdomains **without brute-force by default.**

```bash
sublist3r -d example.com -p 80,443
```

| Short Form | Long Form    | Description                                             |
| ---------- | ------------ | ------------------------------------------------------- |
| -d         | --domain     | Domain name to enumerate subdomains of                  |
| -b         | --bruteforce | Enable the subbrute bruteforce module                   |
| -p         | --ports      | Scan the found subdomains against specific tcp ports    |
| -v         | --verbose    | Enable the verbose mode and display results in realtime |
| -t         | --threads    | Number of threads to use for subbrute bruteforce        |
| -e         | --engines    | Specify a comma-separated list of search engines        |
| -o         | --output     | Save the results to text file                           |
| -h         | --help       | show the help message and exit                          |

{% embed url="https://www.youtube.com/watch?v=VytCL2ujjcA" %}

[^1]: 
