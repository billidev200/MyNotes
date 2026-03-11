# Internal Network Scan

## Netdiscover

#### 🔧 What `netdiscover` Does:

* Performs **ARP scanning** on a local subnet.
* Discovers live hosts (IP and MAC addresses).
* Identifies hardware vendors based on MAC address prefixes.

```bash
netdiscover [options]
```

| Option           | Description                                            |
| ---------------- | ------------------------------------------------------ |
| `-i <interface>` | Interface to use (e.g., eth0, wlan0)                   |
| `-r <range>`     | Scan a specific range (e.g., 192.168.1.0/24)           |
| `-l <file>`      | Scan using IP list from a file                         |
| `-p`             | Passive mode – no ARP requests are sent, listens only  |
| `-m <MAC mask>`  | MAC address filter (e.g., 00:00:00:FF:FF:FF)           |
| `-n`             | Do not resolve hostnames                               |
| `-c <count>`     | Number of times to scan each host                      |
| `-s <delay>`     | Delay between each ARP request (in milliseconds)       |
| `-t <time>`      | Sleep time between each network sweep (in seconds)     |
| `-d`             | Ignore home config files (ignore netdiscover.conf)     |
| `-f`             | Enable fast mode – skips known hosts faster            |
| `-S`             | Enable sleep mode (passive until activity is detected) |
| `-N`             | Do not print header                                    |
| `-P`             | Print results in a format suitable for parsing         |
| `-h`             | Show help screen                                       |
