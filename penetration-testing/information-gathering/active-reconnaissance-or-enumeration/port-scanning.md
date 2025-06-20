---
layout:
  title:
    visible: true
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

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
nmap -sV $ipAddress
```

banner grabbing

```bash
nmap  --script banner $ipAddress
```

Show Operating System

```bash
nmap -O $ipAddress
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

```bash
qnmap --script scriptexmaple or script1 script2
```

```bash
nmap --script ftp-* (runs all scripts)
```

</details>

***

## **WebMap**

Save nmap scans xml reports

{% embed url="https://github.com/SabyasachiRana/WebMap" %}

{% embed url="https://www.youtube.com/watch?pp=ygUGV0VCTUFQ&t=603s&v=SoEIDNnOCGY" %}

***

## Rustscan





