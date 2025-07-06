# Port Scanning

## Nmap

<details>

<summary>Scan <strong>Commands</strong></summary>

ICMP echo | Ping swip

{% code fullWidth="true" %}
```bash
nmap -sn $ipAddress
```
{% endcode %}

TCP connect scan

```bash
nmap -sT $ipAddress
```

TCP SYN scan Stealth

```bash
nmap -sS $ipAddress
```

UDP scan

```bash
nmap -sU $ipAddress
```

Aggressive scan

```bash
nmap -A $ipAddress
```

Fast Most commonly ports

```bash
nmap -F $ipAddress
```

Scan all ports

```bash
nmap -p- $ipAddress
```

Scan whole subnet

```javascript
nmap 192.168.0.0/24
```

***

**Misc**

Custom Scan

```bash
nmap -p 443 $ipAddress
```

Show only open ports

```bash
nmap --open $ipAddress
```



</details>

<details>

<summary>Scan Output</summary>

Verbose increases the level of detail

```bash
nmap -vv $ipAddress
```

```bash
nmap -v $ipAddress
```

Tells reason

```bash
nmap --reason $ipAddress
```

</details>

<details>

<summary>Firewall | IPS/IDS Invasion</summary>

Inverse XMAS scan | Only Linux

```bash
nmap -sX $ipAddress
```

Fin scan  | Only Linux

```bash
nmap -sF $ipAddress
```

Null scan | Only Linux

```bash
nmap -sN $ipAddress
```

Scan Speed adjust

```bash
nmap -T0 -T1 -T2 -T3 -T4 -T5 $ipAddress
```

**Decoy Firewall Evasion**

• -D ‘’ip1 or ip1,ip2’’ or RND:’’number’’ (don’t scan all 65,535, only what you need) and going low and slow to evade IDS and SIEM traffic flow detections)

Packet Fragmentation to 8 bytes

```bash
nmap -f $ipaddress
```

</details>

<details>

<summary>Firewall Detection</summary>

ACK Probing

```bash
nmap -sA $ipAddress
```

</details>

<details>

<summary>Vulnerabilty scanning</summary>

```bash
nmap  --scripts vulners $ipAddress
```

</details>

<details>

<summary>Service Detection | OS</summary>

Show Version

```bash
nmap -sV --version-intensity 5 target-ip
```

```bash
nmap -sV $ipAddress
```

| Intensity Level | Description             |
| --------------- | ----------------------- |
| 0               | No version detection    |
| 1               | Light scan (fast)       |
| 2-6             | Moderate levels         |
| 7               | Default (detailed scan) |
| 8-9             | Very intense, slow scan |

banner grabbing

```bash
nmap  --script banner $ipAddress
```

Show Operating System

```bash
nmap -O $ipAddress
```

**`osscan-guess`** is an option in Nmap that **enables aggressive OS detection guessing**.

```bash
nmap -O --osscan-guess target-ip
```

</details>

<details>

<summary>Speed</summary>

Scan Speed adjust

```bash
nmap -T0 -T1 -T2 -T3 -T4 -T5 $ipAddress
```

</details>

<details>

<summary>Misc</summary>

Traceroute&#x20;

```bash
nmap  --traceroute $ipAddress
```

Save Results

```bash
nmap -oG exmaple.txt > ‘’path’’ $ipAddress
```

Nmap update Database

```bash
nmap --script-updatedb
```

</details>

<details>

<summary>Using script</summary>

```
nmap -sC   (Runs defualt scripts)
```

```bash
nmap --script scriptexmaple or script1 script2
```

```bash
nmap --script ftp-* (runs all scripts)
```

</details>

**Scan saving**

| Format   | Nmap Option | Metasploit Support |
| -------- | ----------- | ------------------ |
| **XML**  | `-oX`       | ✅ Fully supported  |
| Normal   | `-oN`       | ❌ Not supported    |
| Grepable | `-oG`       | ❌ Not supported    |
| JSON     | `-oJ`       | ❌ Not supported    |

***

## **WebMap**

Save nmap scans xml reports

{% embed url="https://www.youtube.com/watch?embeds_referring_euri=https://cdn.iframe.ly/&source_ve_path=MjM4NTE&time_continue=603&v=SoEIDNnOCGY" %}

{% embed url="https://github.com/SabyasachiRana/WebMap" %}

***

## massscan

⚡ **Masscan** – The Fastest Port Scanner

**Masscan** is a **lightning-fast, active** network port scanner, similar to Nmap, but designed for **high-speed Internet-wide scanning**. It can scan the entire IPv4 address space in **minutes** using a custom TCP/IP stack.

🚀 Key Features

| Feature                         | Description                                    |
| ------------------------------- | ---------------------------------------------- |
| ⚡ **Extremely fast**            | Can scan millions of IPs per second            |
| 🔧 Custom TCP/IP stack          | Doesn’t rely on OS networking – very efficient |
| 🔍 Port scan only               | Does **not do service/version detection**      |
| 🛠️ Output compatible with Nmap | Can generate XML output like Nmap              |

💻 Basic Syntax

```bash
masscan -p<ports> <target-range> --rate <packets-per-second>
```

📘 **Masscan Command Reference Table**

| 🔢 # | 📝 **Purpose**                           | 💻 **Command**                                      |
| ---: | ---------------------------------------- | --------------------------------------------------- |
|    1 | Scan **port 80** on a subnet             | `sudo masscan -p80 192.168.1.0/24`                  |
|    2 | Scan **multiple ports**                  | `sudo masscan -p22,80,443 192.168.1.0/24`           |
|    3 | Scan **all ports (0–65535)**             | `sudo masscan -p0-65535 192.168.1.0/24`             |
|    4 | Scan **entire IPv4 Internet** (⚠️)       | `sudo masscan -p80 0.0.0.0/0 --rate 100000`         |
|    5 | Set **custom rate**                      | `sudo masscan -p80 192.168.1.0/24 --rate 5000`      |
|    6 | Output to **grepable text file**         | `sudo masscan -p80 192.168.1.0/24 -oG output.txt`   |
|    7 | Output to **XML (Nmap-compatible)**      | `sudo masscan -p80 192.168.1.0/24 -oX output.xml`   |
|    8 | Scan from a **list of targets**          | `sudo masscan -p80 -iL targets.txt`                 |
|    9 | Specify **network interface**            | `sudo masscan -p80 192.168.1.0/24 --interface eth0` |
|   10 | Scan and grab **service banners** (beta) | `sudo masscan -p80 192.168.1.0/24 --banners`        |
|   11 | Enable **debug output**                  | `sudo masscan -p80 192.168.1.0/24 --debug`          |
|   12 | Scan and output in **binary format**     | `sudo masscan -p80 192.168.1.0/24 -oB results.bin`  |
|   13 | Read and convert **binary output**       | `masscan --readscan results.bin -oX output.xml`     |

***

## rustscan





