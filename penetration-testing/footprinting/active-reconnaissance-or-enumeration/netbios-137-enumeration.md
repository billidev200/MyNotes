# Netbios/137 Enumeration

## Nbtscan

Basic `nbtscan` Command

```bash
nbtscan [options] <target>
```

* **`<target>`**: The IP address or range of IP addresses you want to scan (e.g., `192.168.1.0/24` for a subnet).
* **`[options]`**: Optional flags for more specific scans (e.g., specifying ports).

#### **Limitations of `nbtscan`**

* Works only on **local networks** or networks with **NetBIOS** exposed (e.g., older Windows versions).
* **Firewall rules** may block or limit responses, so ensure no firewall blocks port `137` (the default NetBIOS port) or `139`.
* It doesn’t always work on **modern Windows versions** or in **highly segmented networks**.

| **Command** | **Description**                                                    | **Example**                |
| ----------- | ------------------------------------------------------------------ | -------------------------- |
| nbtscan     | Basic scan of a single IP or network range for NetBIOS information | nbtscan 192.168.1.5        |
| nbtscan -r  | Scan a range of IPs for NetBIOS details                            | nbtscan -r 192.168.1.0/24  |
| nbtscan -v  | Verbose mode to display detailed output                            | nbtscan -v 192.168.1.0/24  |
| nbtscan -s  | Specify a specific port for NetBIOS scan (default is 137)          | nbtscan -s 139 192.168.1.1 |
| nbtscan -h  | Show help and available options                                    | nbtscan -h                 |

* **`nbtscan`** is a simple tool for scanning **NetBIOS** names and related information over TCP/IP.
* Use it to identify devices on local networks, especially in environments with **Windows** machines.
* Scans typically reveal **machine names**, **workgroups**, and **network-related info**.



{% embed url="https://www.youtube.com/watch?v=sXqT95eIAjo" %}
