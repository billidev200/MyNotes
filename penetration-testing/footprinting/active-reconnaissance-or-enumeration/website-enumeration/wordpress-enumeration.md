# WordPress Enumeration

## Wpscan

**Basic Usage**: Scan a WordPress site for vulnerabilities.

```bash
wpscan --url http://example.com
```

<details>

<summary>Enumeration</summary>

**Enumerate Users**: Discover user accounts on a WordPress site.

```bash
wpscan --url http://example.com --enumerate u
```

**Enumerate Plugins**: Discover plugins installed on a WordPress site.

```bash
wpscan --url http://example.com --enumerate p
```

**Enumerate Timthumb Vulnerabilities**: Enumerate vulnerable Timthumbs.

```bash
wpscan --url http://example.com --enumerate t
```

**Enumerate All (Users, Plugins, Themes, Timthumb)**: Enumerate everything at once.

```bash
wpscan --url http://example.com --enumerate u,p,t,tt
```

**Scan for Sensitive Files**: Look for sensitive files that may be exposed (like `wp-config.php` or backups).

```bash
wpscan --url http://example.com --enumerate wp-config
```

</details>

<details>

<summary>Vulnerability scanning</summary>

**Check Plugin Version**: Check for a specific plugin version and its vulnerabilities.

```
wpscan --url http://example.com --plugin-version-plugin-name=1.2.3
```

**Check for Vulnerabilities**: Check the site for known vulnerabilities based on its version and installed plugins.

```bash
wpscan --url http://example.com --vulns
```

**Show Vulnerability Details**: List all the vulnerabilities found on the target site.

```bash
wpscan --url http://example.com --vuln-detection
```



</details>

<details>

<summary>Password Attack Options</summary>

**Brute-force Attack**: Use a wordlist to perform a brute-force attack to find the password for a user.

```bash
wpscan --url http://example.com --username admin --passwords /path/to/wordlist.txt --brute-force
```

**Brute-force for Multiple Users**: Perform a brute-force attack on multiple users (e.g., `admin`, `user`).

```bash
wpscan --url http://example.com --users admin,user --passwords /path/to/wordlist.txt --brute-force
```

**Use the Default Wordlist**: Use the default password wordlist provided by WPScan.

```bash
wpscan --url http://example.com --username admin --brute-force --wordlist /usr/share/wordlists/rockyou.txt
```

**Limit Brute Force Attempts**: Limit the number of brute force attempts to reduce impact on the target.

```
wpscan --url http://example.com --username admin --passwords /path/to/wordlist.txt --brute-force --max-login-attempts 5
```



</details>

<details>

<summary>Advanced Commands</summary>

**Detect WP Version**: Identify the WordPress version used on the site.

```bash
wpscan --url http://example.com --no-banner
```

Scan for SSL/HTTPS Configuration: Check the SSL/TLS configuration of the website.

```bash
wpscan --url https://example.com --ssl-check
```

</details>

<details>

<summary>Proxy</summary>

```bash
wpscan --url http://example.com --proxy http://127.0.0.1:8080
```

</details>

<details>

<summary>Additional Options</summary>

* wpscan --version
* wpscan --help

**Exclude URLs from Scan**: Exclude specific URLs from being scanned.

```bash
wpscan --url http://example.com --exclude /wp-login.php,/wp-admin/
```

**Scan a Specific Directory**: Scan a specific directory for WordPress installations.

```bash
wpscan --url http://example.com/wordpress/
```

**Authentication Token**: If required, authenticate using an API token (e.g., for accessing the WPScan vulnerability database).

```bash
wpscan --url http://example.com --api-token your_token_here
```

</details>

***

## Nmap scripts

Enumerates WordPress users from the target site.

```bash
nmap --script http-wp-users
```

Enumerates WordPress plugins and users to detect potential security issues.

```bash
nmap --script http-wordpress-enum
```
