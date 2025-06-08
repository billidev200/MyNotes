# Firewall config

## iptables

Basic syntax

```bash
sudo iptables [TABLE] COMMAND [CHAIN] [MATCHES] [TARGET]
```

* If no table is specified, it uses the default **filter** table.
* `COMMAND` examples: `-A` (append), `-I` (insert), `-D` (delete), `-L` (list), `-F` (flush).

List current rules (default filter table)

* `-L`: List rules
* `-v`: Verbose (show packet/byte counts)
* `-n`: Numeric output (no DNS resolution)

Allow incoming SSH (port 22)

* `-A INPUT`: Append rule to INPUT chain
* `-p tcp`: Protocol TCP
* `--dport 22`: Destination port 22
* `-j ACCEPT`: Jump to ACCEPT target

**Drop all incoming traffic from a specific IP**

```bash
sudo iptables -A INPUT -s 192.168.1.100 -j DROP
```

#### Delete a rule

* By rule specification (same as adding but with `-D`):

```bash
sudo iptables -D INPUT -p tcp --dport 22 -j ACCEPT
```

### 🔹 Notes

* `iptables` works only for IPv4; for IPv6 use `ip6tables`.
* For easier management, many use front-ends like `ufw` or `firewalld`.
* On newer Linux systems with **nftables**, `iptables` might be a compatibility layer.

🔹 **Example:** Basic Firewall Setu

```bash
sudo iptables -P INPUT DROP           # Default policy: drop all incoming
sudo iptables -P FORWARD DROP         # Drop forwarded packets
sudo iptables -P OUTPUT ACCEPT        # Allow all outgoing

sudo iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT  # Allow replies
sudo iptables -A INPUT -p tcp --dport 22 -j ACCEPT                    # Allow SSH
sudo iptables -A INPUT -p tcp --dport 80 -j ACCEPT                    # Allow HTTP
sudo iptables -A INPUT -p tcp --dport 443 -j ACCEPT                   # Allow HTTPS
```

## ufw

sit on top of iptables make it easier

| Command                  | Description                    |
| ------------------------ | ------------------------------ |
| `sudo ufw enable`        | Enable firewall                |
| `sudo ufw disable`       | Disable firewall               |
| `sudo ufw status`        | Show current rules/status      |
| `sudo ufw allow <port>`  | Allow incoming traffic on port |
| `sudo ufw deny <port>`   | Deny incoming traffic on port  |
| `sudo ufw delete <rule>` | Delete a rule                  |
| `sudo ufw reset`         | Reset to default (flush rules) |

Allow incoming traffic on a port (e.g., SSH 22)

```bash
sudo ufw allow 22
```

```bash
sudo ufw allow ssh
```

Allow a range of ports

```bash
sudo ufw allow 1000:2000/tcp
```

Allow UDP traffic on a port

```bash
sudo ufw allow 123/udp
```

**Basic Commands**

Enable the firewall

```bash
sudo ufw enable
```

Disable the firewall

```bash
sudo ufw disable
```

**Default Policies**

Set default incoming policy to deny (recommended)

```bash
sudo ufw default deny incoming
```

Set default outgoing policy to allow

```bash
sudo ufw default allow outgoing
```

