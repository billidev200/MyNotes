---
description: Tools used for passive reconnaissance
---

# Tools

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



{% embed url="https://www.youtube.com/watch?v=VytCL2ujjcA" %}

[^1]: 
