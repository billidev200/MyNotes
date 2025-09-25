# Web Directory/Subdomain Enumeration/Files

<figure><img src="../../../../../../.gitbook/assets/HttpStatusCode (3).png" alt=""><figcaption></figcaption></figure>

{% hint style="warning" %}
NEVER USE DEFAULT USER AGENT OPSEC!!!!!
{% endhint %}

## gobuster

DNS Bruteforce method

Basic Syntax

```bash
gobuster <mode> -u <URL> -w <wordlist> [options]
```

* `<mode>`: The type of enumeration you want to perform.
* `-u <URL>`: The target URL.
* `-w <wordlist>`: The wordlist file for brute-forcing.

**Modes**

Directory Enumeration

* `dir`

<pre class="language-bash"><code class="lang-bash"><strong>gobuster dir -u &#x3C;URL> -w &#x3C;wordlist> [options]
</strong></code></pre>

Subdomain Enumeration&#x20;

* `dns`

```
gobuster dns -u <URL> -w <wordlist> [options]
```

Virtual Host Discovery&#x20;

* `vhost`

```bash
gobuster vhost -u <URL> -w <wordlist> [options]
```

TFTP enumeration (Trivial File Transfer Protocol)

* `tftp`

```bash
gobuster tftp -u <URL> -w <wordlist> [options]
```

Fuzzing

* `fuzz`

```bash
gobuster fuzz -u "http://example.com/FUZZ" -w <wordlist>
```

**More**

* shows the current version  `version`
* Uses TFTP enumeration mode  `tftp`
* Uses aws bucket enumeration mode `s3`
* Uses gcs bucket enumeration mode `gcs`

**Common commands**

* Verbose `-v`

| Option                | Description                                         |
| --------------------- | --------------------------------------------------- |
| `-u <URL>`            | Target URL (for `dir`, `vhost`, `fuzz`).            |
| `-d <domain>`         | Target domain (for `dns`).                          |
| `-w <wordlist>`       | Path to the wordlist file.                          |
| `-o <output.txt>`     | Save output to a file.                              |
| `-q`                  | Quiet mode (only shows results).                    |
| `-t <threads>`        | Number of threads (default: `10`).                  |
| `--timeout <seconds>` | Set request timeout (default: `10s`).               |
| `-k`                  | Skip SSL certificate verification.                  |
| `-s <status codes>`   | Show only specific HTTP status codes.               |
| `-x <extensions>`     | Test specific file extensions (e.g., `.php,.html`). |
| `-r`                  | Follow redirects.                                   |

***

## Sublist3r

OSINT subdomain discovery method

<figure><img src="../../../../../../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt="" width="509"><figcaption></figcaption></figure>

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

***

## dirb

***

## Nmap scripts

Find hidden directories\\

```bash
nmap --script http-enum <target>
```

```bash
nmap --script http-robots.txt
```

***

## OSINT - SSL/TLS Certificates Subdomain

When an SSL/TLS (Secure Sockets Layer/Transport Layer Security) certificate is created for a domain by a CA (Certificate Authority), CA's take part in what's called "Certificate Transparency (CT) logs". These are publicly accessible logs of every SSL/TLS certificate created for a domain name. The purpose of Certificate Transparency logs is to stop malicious and accidentally made certificates from being used. We can use this service to our advantage to discover subdomains belonging to a domain, sites like [https://crt.sh](https://crt.sh) offer a searchable database of certificates that shows current and historical results.

***

## OSINT - Search Engines Subdomain

Search engines contain trillions of links to more than a billion websites, which can be an excellent resource for finding new subdomains. Using advanced search methods on websites like Google, such as the `site: filter`, can narrow the search results. For example, `site:*.domain.com -site:www.domain.com` would only contain results leading to the domain name domain.com but exclude any links to www.domain.com; therefore, it shows us only subdomain names belonging to domain.com.

***

## Virtual Hosts

{% embed url="https://www.youtube.com/watch?v=qksFm0HaBN0" %}
