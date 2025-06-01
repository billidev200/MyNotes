# WAF/IDS/IPS Enumaration/Detection

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
