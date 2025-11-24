# Web Cache Poisoning

## **Web Cache Poisoning**

Web Cache Poisoning is when an attacker **injects malicious content** into a cached page, so **all users** who visit the page receive the attacker’s payloads

**Step 1 — Attacker sends a crafted request:**

```
https://example.com/?callback=<script>alert(1)</script>
```

**Step 2 — Server puts the `callback` parameter into the response (like in JSONP or reflected output).**

**Step 3 — Cache stores the poisoned response.**

**Step 4 — Every user who visits:**

```
https://example.com/
```

…gets the stored **malicious** page:

* XSS
* Redirect
* Fake login
* CSRF trigger
* malware links
