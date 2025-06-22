---
description: >-
  A zone transfer vulnerability happens when a DNS server is misconfigured,
  allowing unauthorized clients to perform AXFR (zone transfer) requests.
---

# Zone Transfer

#### 🛡️ Zone Transfer in Hacking / Pentesting

In hacking or penetration testing, a **Zone Transfer (AXFR)** is a technique used during **reconnaissance** to extract **all DNS records** for a domain — including subdomains, mail servers, and internal hosts.

🧨 Why Zone Transfer Matters in Hacking

* It's a **goldmine** of information if successful.
* It reveals **internal infrastructure** (like `dev.example.com`, `vpn.example.com`, `staging-db.example.com`).
* Can help attackers plan more focused attacks (e.g., phishing, brute-force, or exploitation).

#### 📦 What Are BIND Versions?

**BIND** (Berkeley Internet Name Domain) is the most widely used **DNS server software** on the Internet. It’s developed and maintained by **ISC (Internet Systems Consortium)**.

A **BIND version** refers to a specific **release of the BIND software**, each containing:

* New features
* Security patches
* Bug fixes
* Performance improvements

## dnsenum

`dnsenum` is a **Perl-based DNS enumeration tool** used by penetration testers and red teamers to gather detailed DNS information about a domain. It helps discover:

* Name servers
* MX records
* Subdomains
* Zone transfers (AXFR)
* Reverse DNS records
* BGP AS information

🚀 Example: Full Enumeration with Subdomain Brute-force

```bash
dnsenum example.com --enum -f /usr/share/wordlists/dnsmap.txt
```

This will:

* Find NS and MX records
* Attempt zone transfer
* Brute-force subdomains using the wordlist
* Perform reverse lookups

***

🛠️ **Common Options**

| Option               | Description                                                  |
| -------------------- | ------------------------------------------------------------ |
| `-f <wordlist>`      | Use a file to brute-force subdomains                         |
| `--enum`             | Enable full enumeration (bruteforce + AXFR + reverse lookup) |
| `--threads <number>` | Number of parallel threads (faster brute-force)              |
| `-r <start-end>`     | Reverse DNS lookup for an IP range                           |
| `-o <filename>`      | Save output to file                                          |

## Dig command

The `dig` command (short for **Domain Information Groper**) is a powerful DNS lookup tool used to **query DNS servers** and **troubleshoot domain name system issues**.

### **Attempt Zone Transfer**

```bash
dig AXFR @ns1.example.com example.com
```

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

## Fierce

**Fierce** is a **DNS reconnaissance tool** used to discover **subdomains**, **hostnames**, and **misconfigurations** in a target domain. It’s especially useful during the **information gathering phase** of penetration testing.

### ✅ What Fierce Does

| Feature                  | Description                                                |
| ------------------------ | ---------------------------------------------------------- |
| 🔍 Subdomain Discovery   | Brute-forces hostnames using a built-in or custom wordlist |
| 📡 Zone Transfer Attempt | Tries AXFR on name servers (like `dig AXFR`)               |
| 🌐 DNS Record Lookup     | Gathers NS and A records                                   |
| 🔁 Reverse DNS Lookup    | Scans adjacent IPs for reverse DNS entries                 |
| 🛰️ Network Mapping      | Tries to map the domain’s network structure                |

💻 How to Use Fierce

```bash
fierce -dns example.com
```

This will:

* Look up name servers
* Try a zone transfer
* Attempt subdomain brute-force with common names

| Option                     | Description                                    |
| -------------------------- | ---------------------------------------------- |
| `-dns <domain>`            | Target domain                                  |
| `-wordlist <file>`         | Use a custom wordlist                          |
| `-range <x.x.x.x-x.x.x.x>` | Scan reverse DNS across an IP range            |
| `-file <outputfile>`       | Save results to a file                         |
| `-search <keyword>`        | Filter hostnames containing a specific string  |
| `-delay <seconds>`         | Add delay between lookups (useful for stealth) |

### ⚠️ Limitations

* It’s **not stealthy** — sends lots of DNS requests.
* Slower and older than modern tools like `Amass` or `dnsx`.
* Still useful in **CTFs** or **targeted recon**.
