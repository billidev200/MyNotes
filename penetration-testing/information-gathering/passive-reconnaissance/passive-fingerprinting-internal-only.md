# Passive Fingerprinting Internal only

**Fingerprinting** is the process of **gathering information about a system, device, software, or network** to identify it uniquely—just like a human fingerprint. It's a **reconnaissance technique** used both by ethical hakers and attackers.

&#x20;**1. Fingerprinting**

**Definition**: The process of identifying specific **details about a system**, like:

* Operating system
* Web server
* Software versions
* Services
* Network device types

**Can be**:

* **Active** (sending probes with `nmap`, `telnet`)
* **Passive** (sniffing traffic with `p0f`, `Wireshark`)

{% hint style="info" %}
It just active recon with passive way of gaining the info ( OS, Services and versions )
{% endhint %}

## p0f

#### 🔎 What is **p0f**?

* **p0f** is a **passive OS fingerprinting tool**.
* It **sniffs network traffic** and analyzes packets to identify the OS, network distance, and other info — all **without sending any packets**.
* Great for stealthy reconnaissance on a local network.

{% hint style="warning" %}
This only works when conntect to a LAN,  you need to be **on the same Layer 2 network (LAN, subnet, or broadcast domain**
{% endhint %}

1\. Listen on interface `eth0` (default promiscuous mode):

```bash
p0f -i eth0
```

2\. Listen on `wlan0` without promiscuous mode:

```bash
p0f -i wlan0 -p
```

3. Read from a pcap file and log output to a file:

```bash
p0f -r traffic.pcap -o p0f.log
```

4. Verbose mode with logging:

```bash
p0f -i eth0 -v -o output.log
```

| Command / Option | Description                                         | Example                     |
| ---------------- | --------------------------------------------------- | --------------------------- |
| `-i <interface>` | Specify the network interface to listen on          | `p0f -i eth0`               |
| `-p`             | Do **not** put the interface in promiscuous mode    | `p0f -i eth0 -p`            |
| `-r <file>`      | Read packets from a pcap capture file               | `p0f -r capture.pcap`       |
| `-o <file>`      | Output log data to a file                           | `p0f -i eth0 -o output.log` |
| `-v`             | Verbose output, more detailed info                  | `p0f -i eth0 -v`            |
| `-s`             | Show summary statistics when quitting               | `p0f -i eth0 -s`            |
| `-u <user>`      | Run as a specific user after startup (for security) | `p0f -i eth0 -u nobody`     |
| `-P`             | Show OS detection results only (skip other info)    | `p0f -i eth0 -P`            |
| `-h` or `--help` | Show help and usage information                     | `p0f -h`                    |
