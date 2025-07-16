# 1 - Information Gathering

**1. Passive Information Gathering**

* Done **without directly interacting** with the target.
* Goal: Avoid detection.
* Sources:
  * WHOIS records
  * DNS records
  * Social media
  * Job postings
  * Public websites
  * Google hacking (dorking)

**2. Active Information Gathering**

* Involves **direct interaction** with the target.
* Riskier because it can **trigger alerts** or logs.
* Tools/Techniques:
  * Ping, traceroute
  * Port scanning (e.g., Nmap)
  * Banner grabbing
  * OS fingerprinting

#### What is **Footprinting**?

**Footprinting** is a **specific part of Information Gathering** where the goal is to **collect detailed information about a specific target** — like a company, website, or server — **before launching an attack**.

Think of footprinting as **drawing a blueprint** of the target's digital presence.

**OS fingerprinting** is the process of determining the **operating system (OS)** running on a remote device or host by analyzing how it responds to certain network probes or traffic.

There are two main types:

#### 🔍 1. **Active OS Fingerprinting**

* **How it works:** Sends specially crafted packets to a target and analyzes the responses.
* **Tools:** `Nmap`, `XProbe`, `NetScanTools`
* **Example:** Sending a TCP packet with unusual flags and seeing how the host responds. Different OSes respond differently.
* **Pros:** Fast and accurate
* **Cons:** Noisy (can be detected by intrusion detection systems)

***

#### 🕵️ 2. **Passive OS Fingerprinting**

* **How it works:** Observes traffic passively (without sending packets) and analyzes existing data such as TTL, TCP window size, and options.
* **Tools:** `p0f`, `Wireshark`, `Satori`
* **Example:** Sniffing network traffic and inferring OS from the characteristics of packets already being sent.
* **Pros:** Stealthy, undetectable
* **Cons:** Less accurate, requires ongoing traffic

<figure><img src="../../../.gitbook/assets/image (3) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (4) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
