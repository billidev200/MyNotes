---
description: >-
  LFI occurs when a web application allows user input to include files on the
  server without proper validation. The goal is to manipulate the input
  parameter to include sensitive files or files that can
---

# Local File Inclusion (LFI)

The most common place we usually find LFI within is templating engines. In order to have most of the web application looking the same when navigating between pages, a templating engine displays a page that shows the common static parts, such as the `header`, `navigation bar`, and `footer`, and then dynamically loads other content that changes between pages. Otherwise, every page on the server would need to be modified when changes are made to any of the static parts. This is why we often see a parameter like `/index.php?page=about`, where `index.php` sets static content (e.g. header/footer), and then only pulls the dynamic content specified in the parameter, which in this case may be read from a file called `about.php`. As we have control over the `about` portion of the request, it may be possible to have the web application grab other files and display them on the page.

**We add  `../../../`   depending on how deep we are.**

**Example Vulnerable URL:**

```bash
http://example.com/index.php?page=about
```

In this case, the application might be including a file called `about.php`, but the attacker can modify the `page` parameter to include files from the server.

**Basic LFI Payload:**

```bash
http://example.com/index.php?page=../../../../etc/passwd
```

This attempts to read the **`/etc/passwd`** file (on Unix-based systems), which contains user account information.

***

## **LFI Techniques**

**Directory Traversal (Dot-Dot-Slash)**

* **Goal**: Use `../` (dot-dot-slash) to traverse up the directory structure and access files outside the web root.
*   **Example**:

    ```bash
    ../../../../etc/passwd
    ```

**Null Byte Injection (Legacy Vulnerability)**

Some web applications may incorrectly handle file paths containing a null byte (`%00`), terminating the file path and ignoring the extension (e.g., `.php`, `.txt`).

**Example** (Legacy Vulnerability):

```
bashCopy../../../../etc/passwd%00
```

This may bypass security checks by terminating the file extension.

**Adding** `%00`

***

## **Linux Systems**:

* `/etc/passwd`: User account details (on Linux/Unix).
* `/etc/shadow`: Password hashes (if accessible).
* `/etc/hostname`: Hostname of the machine.
* `/var/log/apache2/access.log`: Web server access logs.
* `/var/log/syslog`: System logs.
* `/etc/nginx/nginx.conf`: Nginx configuration file.
* `/proc/self/environ`: Environment variables of the current process.

## **Windows Systems**:

* `C:\Windows\System32\drivers\etc\hosts`
* `C:\xampp\htdocs\phpmyadmin\config.inc.php`
* `C:\Windows\win.ini`

