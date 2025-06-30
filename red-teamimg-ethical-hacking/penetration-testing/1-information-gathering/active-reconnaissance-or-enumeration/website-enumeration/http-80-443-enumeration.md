---
description: https://hacktools.sh/
---

# HTTP 80/443 Enumeration

## Nmap scripts

find hidden directories

```bash
nmap --script http-enum <target>
```

```bash
nmap --script http-robots.txt
```

| **Script Name**         | **Description**                                                                                                   |
| ----------------------- | ----------------------------------------------------------------------------------------------------------------- |
| http-apache-negotiation | Detects Apache server and checks for content negotiation vulnerabilities.                                         |
| http-apache-version     | Retrieves the version of the Apache HTTP Server.                                                                  |
| http-auth-finder        | Attempts to detect and identify web-based authentication methods.                                                 |
| http-auth-ntlm-info     | Attempts to gather information about NTLM authentication from web servers.                                        |
| http-brute              | Brute-forces HTTP authentication using a list of common usernames and passwords.                                  |
| http-csrf               | Detects possible Cross-Site Request Forgery (CSRF) vulnerabilities in web applications.                           |
| http-debug              | Detects web servers with the HTTP debug option enabled.                                                           |
| http-enum               | Enumerates common directories and files on the target web server.                                                 |
| http-headers            | Displays all HTTP response headers from the target web server.                                                    |
| http-iis-webdav-vuln    | Detects if the web server is vulnerable to IIS WebDAV issues.                                                     |
| http-methods            | Enumerates HTTP methods supported by the web server (e.g., GET, POST, PUT, DELETE).                               |
| http-open-proxy         | Detects open HTTP proxy servers.                                                                                  |
| http-passwd             | Tries to extract HTTP passwords or authentication mechanisms.                                                     |
| http-php-version        | Attempts to determine the version of PHP used by the web server.                                                  |
| http-robots.txt         | Extracts paths listed in the robots.txt file (which may contain sensitive directories).                           |
| http-server-header      | Retrieves the Server HTTP header, which can help identify the web server.                                         |
| http-slowloris          | Tries to execute a Slowloris attack against the target web server to identify if it is vulnerable to DoS attacks. |
| http-sql-injection      | Attempts SQL injection against web forms or URL parameters to find SQL injection vulnerabilities.                 |
| http-title              | Retrieves the title of the web page from the tag in the HTML header.                                              |
| http-trace              | Checks if the HTTP TRACE method is enabled, which could lead to security vulnerabilities.                         |
| http-vuln-cve2006-3392  | Detects a vulnerability in older versions of PHP (CVE-2006-3392).                                                 |
| http-vuln-cve2014-3704  | Detects Drupal SQL Injection vulnerability (CVE-2014-3704).                                                       |
| http-vuln-cve2017-5638  | Detects Apache Struts RCE vulnerability (CVE-2017-5638).                                                          |
| http-wp-users           | Enumerates WordPress users from the target site.                                                                  |
| http-wordpress-enum     | Enumerates WordPress plugins and users to detect potential security issues.                                       |
| http-joomla-enum        | Enumerates Joomla! users and versions to identify security risks.                                                 |
| http-xssed              | Detects potential Cross-Site Scripting (XSS) vulnerabilities based on responses from the server.                  |
