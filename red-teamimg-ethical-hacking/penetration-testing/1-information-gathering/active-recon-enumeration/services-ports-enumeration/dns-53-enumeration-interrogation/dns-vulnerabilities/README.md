# DNS vulnerabilities

### ⚠️ 1. **DNS Zone Transfer (AXFR)**

* **What**: Misconfigured name servers allow full zone file download.
* **Impact**: Leaks all DNS records — subdomains, mail servers, internal services.
* **Fix**: Restrict AXFR to trusted IPs (usually secondary DNS servers only).

***

### ⚠️ 2. **DNS Cache Poisoning**

* **What**: Attacker injects false DNS data into a resolver’s cache.
* **Impact**: Redirects users to malicious sites.
* **Fix**: Use DNSSEC, randomize source ports, and ensure proper caching behavior.

***

### ⚠️ 3. **DNS Spoofing / Man-in-the-Middle**

* **What**: Attacker tricks a DNS client into accepting forged DNS responses.
* **Impact**: Traffic hijacking, phishing, malware delivery.
* **Fix**: Use DNSSEC and encrypted DNS protocols (like DoH or DoT).

***

### ⚠️ 4. **DNS Rebinding**

* **What**: Attacker tricks a browser into interacting with internal IPs via malicious DNS records.
* **Impact**: Access to internal-only services through a victim's browser.
* **Fix**: Use same-origin policies, network ACLs, and browser hardening.

***

### ⚠️ 5. **Open DNS Resolvers**

* **What**: DNS server allows anyone on the internet to query it.
* **Impact**: Used for DDoS amplification attacks.
* **Fix**: Restrict resolver access to internal/trusted IPs only.

***

### ⚠️ 6. **Subdomain Takeover**

* **What**: A DNS record points to a service (like GitHub Pages, Heroku) that no longer exists.
* **Impact**: Attacker can claim the orphaned service and hijack the subdomain.
* **Fix**: Regularly audit DNS records; remove or update stale CNAMEs.

***

### ⚠️ 7. **Wildcard DNS Misconfiguration**

* **What**: Misconfigured wildcard entries (e.g., `*.example.com`) resolve all subdomains.
* **Impact**: May enable phishing or subdomain enumeration bypass.
* **Fix**: Use wildcards carefully and validate requests server-side.

***

### ⚠️ 8. **Lack of DNSSEC (DNS Security Extensions)**

* **What**: DNS responses are unauthenticated.
* **Impact**: Vulnerable to spoofing and tampering.
* **Fix**: Enable DNSSEC to cryptographically sign DNS data.

***

### ⚠️ 9. **Information Disclosure via Reverse DNS**

* **What**: PTR records or zone files reveal sensitive naming conventions (e.g., `dev-db.internal.example.com`).
* **Impact**: Assists attackers in mapping internal networks.
* **Fix**: Limit PTR record exposure and use generic naming.

***

### ⚠️ 10. **Slow or Misconfigured DNS Resolvers**

* **What**: Poorly tuned or outdated DNS servers with long TTLs or no rate-limiting.
* **Impact**: Can be used in timing attacks or DoS conditions.
* **Fix**: Update DNS software, rate-limit requests, use timeouts.

***
