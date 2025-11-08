# Stay Anoymous

{% embed url="https://dnsleaktest.com/" %}

## anonsurf

| Command                  | Description                                |
| ------------------------ | ------------------------------------------ |
| `sudo anonsurf start`    | Start anonymized routing through Tor       |
| `sudo anonsurf stop`     | Stop it and restore your normal connection |
| `sudo anonsurf restart`  | Restart Tor routing                        |
| `sudo anonsurf status`   | Show current status                        |
| `sudo anonsurf changeid` | Change your Tor identity (new IP)          |
| `sudo anonsurf myip`     | Check current external IP address          |
| `sudo anonsurf dns`      | Use anonymous DNS                          |
| `sudo anonsurf flush`    | Flush iptables rules if something breaks   |

## macchanger (LAN only)

| Command                                               | Description                                                          |
| ----------------------------------------------------- | -------------------------------------------------------------------- |
| `sudo macchanger -r <interface>`                      | Assign a **random MAC address**                                      |
| `sudo macchanger --mac=XX:XX:XX:XX:XX:XX <interface>` | Set a **specific MAC address**                                       |
| `sudo macchanger -p <interface>`                      | **Reset** to the original (factory) MAC                              |
| `sudo macchanger -s <interface>`                      | **Show** current MAC address                                         |
| `sudo macchanger -a <interface>`                      | Assign a **random MAC with the same vendor prefix**                  |
| `sudo macchanger -A <interface>`                      | Assign a **completely random MAC address** (including vendor prefix) |
| `sudo macchanger -h`                                  | Show **help** and available options                                  |

{% embed url="https://www.youtube.com/watch?index=5&list=PLBf0hzazHTGOh6JBKc8WkpyuZgDPW6yTk&v=jqrd9Ba3VOc" %}
