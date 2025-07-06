# RDP/3389 Enumeration

#### 🔍 **What Can Be Enumerated**

* **Open RDP Port (TCP 3389)**
* **RDP Version Information**
* **Network Level Authentication (NLA) status**
* **Hostname and Domain Information**
* **Username Enumeration**
* **Clipboard / Device Redirection support**
* **Session Info (connected users, sessions)**

🔐 **What is Network Level Authentication (NLA)?**

🔹 Normal RDP Flow (Without NLA):

1. You connect to the RDP server.
2. A full Windows login screen is presented.
3. You enter credentials.
4. If correct, the session is established.

**Problem:** This consumes server resources **before** authentication and exposes the login UI to the network — potentially allowing **username enumeration**, brute-force attacks, or denial of service.

✅ **Benefits of NLA**

* 🛡️ **Prevents unauthenticated RDP session creation**
* 🚫 **Reduces exposure to brute-force and DoS**
* 🔍 **Blocks some RDP exploits (e.g., BlueKeep)**
* 🔒 Uses **stronger authentication mechanisms**

***

⚠️ **Limitations**

* Requires RDP clients that support NLA (Windows Vista/7+, or compatible 3rd-party clients)
* Makes RDP **brute-forcing harder**, but not impossible if creds are known
* Sometimes causes issues in **older RDP clients or misconfigured systems**

## Bruteforce

{% content-ref url="../../../../password-cracking/service-brute-force-online/" %}
[service-brute-force-online](../../../../password-cracking/service-brute-force-online/)
{% endcontent-ref %}

## Nmap scripts

```
nmap -p 3389 --script rdp-enum-encryption <ip>
```

```
nmap -p 3389 --script rdp-ntlm-info <target>
```

## Metasploit Auxiliary

* rdp-scanner

## xfreerdp linux

Use rdp on linux to connect to windows pc

```
xfreerdp /v:<target_ip_or_hostname> /u:<username> /p:<password>
```

🧩 **Common Options**

| Option                 | Description                                          |
| ---------------------- | ---------------------------------------------------- |
| `/v:<host>`            | Target RDP server IP or hostname                     |
| `/u:<username>`        | Username                                             |
| `/p:<password>`        | Password                                             |
| `/cert:ignore`         | Ignore certificate validation (bypass TLS cert)      |
| `/f`                   | Fullscreen                                           |
| `/size:WxH`            | Set resolution (e.g., `/size:1280x720`)              |
| `/clipboard`           | Enable clipboard sync                                |
| `/drive:<name>,<path>` | Share local folder (e.g., `/drive:share,/home/user`) |
| `/sound:sys:alsa`      | Enable sound over ALSA                               |
