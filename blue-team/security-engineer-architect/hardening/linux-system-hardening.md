---
icon: linux
---

# Linux System Hardening

## Physical Security

### Boot protection

* Defence-in-Depth means layering security; the first layer is **physical security**.
* If an attacker gains physical access they can do simple, powerful attacks (e.g., remove a disk drive or reset system credentials).
* Even with strong account passwords, physical access often lets an attacker use the bootloader (GRUB) to reset root — hence the phrase **“boot access = root access.”**
* Add hardware/firmware protections where practical: **BIOS/UEFI boot passwords** can stop unauthorized boots (useful for personal machines; impractical for servers because someone must be physically present).
* On Linux, you can protect GRUB by creating a GRUB password (example tool: `grub2-mkpasswd-pbkdf2`), which generates a PBKDF2 hash to add to GRUB’s config and prevents unauthorized access to advanced boot options.
* GRUB passwords are **not** meaningful for many cloud VMs or remotely hosted systems because you don’t control the physical console.
* **Bottom line:** enforce physical security first; add bootloader/firmware passwords as an extra layer — and prepare additional controls (e.g., plans for stolen disks) because passwords alone won’t stop physical-theft scenarios.

PBKDF2 stands for [**Password-Based Key Derivation Function 2**](https://www.google.com/search?client=firefox-b-d\&q=Password-Based+Key+Derivation+Function+2\&mstk=AUtExfA9pYuOq-lHtieBohYx2_we3S1wLFip3RYUcCPtJMQtHSLpVtoeVLKpGsQpMBp60k4kivu1lCuKZ9B5chO2IPrSdXABdvSj45H2_Oopjr0bVAXo154UdxQqatqEgNd5YagOhw7Piirh6FJEDfj4xS1XOC47SWjn8afDAhIf_8DhdhewjHJP4hPzhOW7xmfMpt2qJVJ7t94A8ijaNyj9iYya6g\&csui=3\&ved=2ahUKEwisgvCej-OQAxUMBdsEHbs1HKAQgK4QegQIARAE). It's a cryptographic algorithm that takes a password, a salt, and a set number of iterations to generate a secure, derived key, primarily used to protect passwords from brute-force attacks by making the hashing process computationally expensive

```bash
root@AttackBox# grub2-mkpasswd-pbkdf2
Enter password: 
Reenter password: 
PBKDF2 hash of your password is grub.pbkdf2.sha512.10000.534B77859C13DCF............etc
```

### Filesystem Partitioning and Encryption

* **Encryption** protects data by making it unreadable without the correct decryption key.
* If an attacker gains **physical access** (e.g., steals your laptop), encrypted data remains useless to them—like a broken drive.

**LUKS (Linux Unified Key Setup)**

* Most modern Linux systems use **LUKS** for full-disk encryption.
* A LUKS-encrypted disk includes:
  * **LUKS phdr (Partition Header):** Stores info such as UUID, cipher type/mode, key length, and master key checksum.
  * **Key Material (KM1–KM8):** Each slot stores a copy of the **master key** encrypted with a different user password.
  * **Bulk Data:** Actual user data encrypted with the master key.

## Firewall

**Firewall Policies**

Before configuring a firewall, you need to decide upon the firewall policy. You might be the decision maker regarding the firewall policy or an enforcer of an existing security policy that covers firewall configuration. It all depends on the system you are protecting.

We will not go into security policies as this is outside the scope of this room. We will mention that the two main approaches are:

* Block everything and allow certain exceptions.
* Allow everything and block certain exceptions.

⚙️ **Linux Firewall Frameworks**

**1. Netfilter**

* Built into the Linux kernel.
* Requires a **front-end** like `iptables` or `nftables` to configure filtering rules.

**2. nftables**

* Replaces iptables in newer kernels (3.13+).
* More efficient and scalable.
* Example configuration (simplified):

**3. UFW (Uncomplicated Firewall)**

* A user-friendly front-end for iptables.
* Simplifies rule management with easy commands:

## Remote Access

Providing remote access to a system is a very convenient way to access your system and files when you are not physically present at the target system’s keyboard. However, this also means that you are voluntarily providing a service that attackers will target. Common attacks include:

1. Password sniffing
2. Password guessing and brute-forcing
3. Exploiting the listening service

* Exposed SSH servers are constantly scanned and brute-forced by attackers trying common usernames/passwords (often `root` + weak passwords).
* **Main goals:** stop direct root login and remove password-based logins so guessing attacks fail.

**Practical hardening steps**

**Disable root SSH login** (force users to connect as non-root):\
Add to `/etc/ssh/sshd_config`&#x20;

```bash
PermitRootLogin no
```

**Force public-key authentication and disable passwords:**

Forcing **public-key authentication** and **disabling password logins** in SSH dramatically improves security because it removes the biggest weakness in remote authentication — human-chosen passwords.

```
PubkeyAuthentication yes
PasswordAuthentication no
```

## Securing User Accounts

The `root` account carries with it tremendous power and hence risk. You are at risk of rendering your system unbootable with a simple mistake. Using a non-root account for everyday work is recommended to avoid sabotaging your system. However, `root` privileges are still needed for system maintenance, installing/removing software packages, and updating/configuring the system.

#### 1. Don’t log in as `root` for daily work

* Use a regular user for everyday tasks to avoid accidental system damage.
* Keep `root` for maintenance only.

#### 2. Use `sudo` for administrative tasks

* Add an admin user to the distro’s sudoers group so they can run privileged commands with `sudo`.

#### 3. Disable direct `root` logins (optional)

* Make `root` non-login by changing its shell in `/etc/passwd`:

```bash
root:x:0:0:root:/root:/bin/bash
→ change to:
root:x:0:0:root:/root:/sbin/nologin
```

4. **Enforce a strong password policy (libpwquality / PAM)**

* Use `libpwquality` (PAM) to force password complexity and rotation.
* Config files:
  * RedHat/Fedora: `/etc/security/pwquality.conf`
  * Debian/Ubuntu: `/etc/pam.d/common-password` (with `libpam-pwquality` installed)
* Example options in `/etc/security/pwquality.conf`:

```bash
difok=5      # new password must differ by at least 5 characters from old
minlen=10    # minimum length 10
minclass=3   # require 3 character classes (upper/lower/digits/symbols)
retry=2      # prompt up to 2 times before failure
```

5. **Disable unused or service accounts**

Disable human accounts no longer needed by setting their shell to `/sbin/nologin` in `/etc/passwd`:

## Software and Services

1. **Disable Unnecessary Services**
2. **Block Unneeded Network Ports**
3. **Avoid Legacy Protocols**

Instead of Telnet, the SSH protocol is now widely available. For example, the Secure File Transfer Protocol (SFTP) protocol provides a great alternative to the TFTP protocol. The critical point is that a secure alternative is selected and used.

1. **Remove Identification Strings**

Whenever you connect to a remote server, it usually replies with its version number. This information would reveal various information to the attacker, such as the name of the server/program, the version number, and the host operating system.

## Audit and Log Configuration

Most log files on Linux systems are stored in the **`/var/log`** directory. Here are a few of the logs that can be referenced when looking into threats:

* `/var/log/messages` - a general log for Linux systems
* `/var/log/auth.log` - a log file that lists all authentication attempts (Debian-based systems)
* `/var/log/secure` - a log file that lists all authentication attempts (Red Hat and Fedora-based systems)
* `/var/log/utmp` - an access log that contains information regarding users that are currently logged into the system
* `/var/log/wtmp` - an access log that contains information for all users that have logged in and out of the system
* `/var/log/kern.log` - a log file containing messages from the kernel
* `/var/log/boot.log` - a log file that contains start-up messages and boot information

We will keep this task short and include only two handy commands for large log files.

* Since new events are appended to the log file, you can view the last few lines using `tail`. For example, `tail -n 12 boot.log` will display the last 12 lines.
* One way to search log lines containing a specific keyword is using the command `grep`. For instance, `grep FAILED boot.log` will only show the lines with the word `FAILED`.

## Update and Upgrade Policies

1. **Regular Updates Are Essential**
2. **Choose Long-Term Supported (LTS) Releases**
3. **Kernel Updates Matter**
4. **Automate Updates**
