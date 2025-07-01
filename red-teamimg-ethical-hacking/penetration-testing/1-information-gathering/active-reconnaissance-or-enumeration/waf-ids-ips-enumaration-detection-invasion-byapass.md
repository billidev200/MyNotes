# WAF/IDS/IPS Enumaration - Detection - Invasion/Byapass

## wafw00f

Detects if a website has a Web Application Firewall (WAF) and what kind it is.

**Basic scan:**

```bash
wafw00f example.com
```

Verbose Mode (More Details):

```bash
wafw00f -v example.com
```

Aggresive scan

```bash
wafw00f -a example.com
```

***

## Nmap scripts

Detect WAF

```bash
nmap --script http-waf-detect <target>
```

Tries to detect the presence of a web application firewall and its type and version.

This works by sending a number of requests and looking in the responses for known behavior and fingerprints such as Server header, cookies and headers values. Intensive mode works by sending additional WAF specific requests to detect certain behaviour.

<pre class="language-bash"><code class="lang-bash"><strong>nmap --script http-waf-fingerprint &#x3C;target>
</strong></code></pre>

Nmap command ACK Probe

```bash
nmap -sA <target>
```

WAF detection **simply determines whether a WAF is protecting a web application**.

#### **🔍 How WAF Detection Works**

* Sending **normal HTTP requests** and checking if the response is **unexpectedly blocked** (e.g., HTTP `403 Forbidden` or `406 Not Acceptable`).
* Looking at **HTTP headers** that indicate WAF usage (e.g., `Server: cloudflare` or `X-Security-Akamai`).
* Sending **malicious payloads** (e.g., SQL injection) to see if they get blocked.
* Based by reposnse

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

🔓 **Common Techniques Hackers Use to Bypass Firewalls**

| **Technique**                           | **Description**                                                                  |
| --------------------------------------- | -------------------------------------------------------------------------------- |
| **1. Port Hopping / Scanning**          | Scanning for **open ports** (e.g., 80, 443) and using those for payloads.        |
| **2. Tunneling**                        | Using protocols like **HTTP(S), DNS, ICMP**, or **SSH** to tunnel traffic.       |
| **3. Payload Encryption / Obfuscation** | Encrypting payloads with tools like `msfvenom`, `Veil`, or custom scripts.       |
| **4. Living-off-the-Land (LotL)**       | Using built-in tools like `PowerShell`, `WMI`, or `Certutil` to avoid detection. |
| **5. Application Layer Attacks**        | Using **malicious web traffic** or **encoded URLs** to sneak through WAFs.       |
| **6. Exploiting Misconfigurations**     | Abusing overly permissive rules (e.g., `allow all outbound`, default settings).  |
| **7. Social Engineering / Phishing**    | Sending **malicious attachments or links** that create outbound connections.     |
| **8. Reverse Shells**                   | Initiating **outbound connections** (which most firewalls allow) to attacker.    |
| **9. Packet Fragmentation**             | Breaking payloads into fragments to confuse or bypass packet inspection.         |
| **10. Domain Fronting / CDN Abuse**     | Masking C2 traffic through **trusted domains** like Cloudflare or Google.        |
|                                         |                                                                                  |
