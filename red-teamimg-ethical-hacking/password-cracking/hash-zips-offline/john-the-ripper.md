# John the Ripper

🔹 1. Basic Syntax

```
john [options] [password‑file]
```

🔹 2. Showing Cracked Passwords

```
john --show [password‑file]
```

`--show`\
Lists all passwords cracked so far (from the “pot” file), with optional account formatting.

🔹 3. Specifying Formats

```
john --format=<format> [password‑file]
```

{% hint style="info" %}
**Note**: John the Ripper’s format support is extensive and grows with each Jumbo patch. To see the absolutely complete and up‑to‑date list, run: `john --list=formats`
{% endhint %}

| **Format Name** | **Description**                               |
| --------------- | --------------------------------------------- |
| descrypt        | Traditional Unix `crypt(3)` DES hashes        |
| bsdicrypt       | BSDI-modified DES hashes                      |
| md5crypt        | FreeBSD/Linux MD5-based crypt hashes          |
| md5crypt‑long   | MD5‑crypt with longer salt support            |
| bcrypt          | Blowfish-based bcrypt hashes                  |
| scrypt          | Scrypt KDF-based hashes                       |
| LM              | Windows LAN Manager hashes                    |
| AFS             | AFS (OpenAFS) DES-based hashes                |
| tripcode        | DES-based Tripcode hashes (e.g. IRC)          |
| AndroidBackup   | Android backup “\*.ab” file hashes            |
| adxcrypt        | ADXCrypt portable database                    |
| agilekeychain   | 1Password Agile Keychain                      |
| aix‑ssha1       | AIX SHA‑1 salted                              |
| aix‑ssha256     | AIX SHA‑256 salted                            |
| aix‑ssha512     | AIX SHA‑512 salted                            |
| andOTP          | andOTP authenticator backups                  |
| ansible         | Ansible Vault                                 |
| argon2          | Argon2i password hashes                       |
| as400‑des       | IBM AS/400 DES hashes                         |
| as400‑ssha1     | IBM AS/400 SHA‑1 salted                       |
| asa‑md5         | Cisco ASA MD5                                 |
| AxCrypt         | AxCrypt                                       |
| AzureAD         | Microsoft Azure AD                            |
| BestCrypt       | Jetico BestCrypt container                    |
| bfegg           | BitLocker FVEK Encrypted Guest Generation Key |
| Bitcoin         | Bitcoin wallet (encrypted)                    |
| BitLocker       | Microsoft BitLocker full-volume encryption    |
| bitshares       | BitShares wallet                              |
| Bitwarden       | Bitwarden CLI / web vault                     |
| BKS             | BouncyCastle “.bks” keystore                  |
| Blackberry‑ES10 | BlackBerry 10 password database               |
| WoWSRP          | World of Warcraft SRP authentication          |
| Blockchain      | Blockchain.com wallet                         |
| chap            | CHAP (PPP)                                    |
| Clipperz        | Clipperz online vault                         |
| cloudkeychain   | Apple iCloud Keychain                         |
| dynamic\_n      | Dynamic formats (auto‑configurable)           |
| cq              | Cisco CQ                                      |
| CRC32           | CRC32 checksums                               |
| sha1crypt       | SHA‑1 based crypt                             |
| sha256crypt     | SHA‑256 based crypt                           |
| sha512crypt     | SHA‑512 based crypt                           |
| Citrix\_NS10    | Citrix NetScaler 10                           |
