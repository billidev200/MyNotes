# DNS/53 Enumeration - Interrogation

## Nmap Scripts

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

***

## Dnsdumpster

{% embed url="https://dnsdumpster.com/" %}

***

## Nslookup

Looks up the IP address for a domain name or finds the domain name for an IP address.

```bash
nslookup example.com
```

By default, [`nslookup` ](#user-content-fn-1)[^1][uses ](#user-content-fn-1)[^1]port **53**, but you can specify a different one:

<pre class="language-bash"><code class="lang-bash"><strong>nslookup -port=5353 example.com
</strong></code></pre>

***

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

## DNS Records

<figure><img src="../../../../../../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../../../../.gitbook/assets/616eb649d651f3d5247443ea_Screen Shot 2021-10-19 at 7.56.23 AM.png" alt=""><figcaption></figcaption></figure>

[^1]: 
