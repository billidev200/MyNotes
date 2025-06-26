# Web Directory/Subdomain Enumeration

## gobuster

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

## Nmap scripts

Find hidden directories\\

```bash
nmap --script http-enum <target>
```

```bash
nmap --script http-robots.txt
```
