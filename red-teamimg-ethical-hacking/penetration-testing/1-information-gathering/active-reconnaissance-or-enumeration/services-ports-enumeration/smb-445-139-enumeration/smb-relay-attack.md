# SMB relay attack

## SMB Relay Attack Explained

***

### 🔍 What is SMB Relay?

An **SMB Relay attack** is a **man-in-the-middle (MITM)** attack that targets the SMB (Server Message Block) protocol used mainly for file and printer sharing on Windows networks.

* Instead of stealing passwords directly, the attacker **relays authentication requests** from one machine to another.
* The attacker acts as a proxy, forwarding authentication data to a target server.
* This allows the attacker to authenticate on the target **without knowing the user’s password**.

***

**SMB Relay attacks typically work best on a LAN (Local Area Network)** because:

* The attacker needs to **position themselves as a man-in-the-middle (MITM)** between the victim and the SMB server to intercept and relay authentication traffic.
* This usually requires the attacker to be on the **same broadcast domain or subnet** to perform ARP spoofing, LLMNR/NBT-NS poisoning, or other MITM techniques.
