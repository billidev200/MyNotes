---
icon: shield
---

# Network Security Protocols

#### DNSSEC

DNSSEC makes it possible to ensure that the DNS response we receive is from the domain owner. To achieve this, DNSSEC requires two main things:

1. The DNS zone owner should sign all DNS records using their private key.
2. The DNS zone publishes its public key so users can check the validity of the DNS records signatures.

#### SSL/TLS Protocol

**Technical Overview - SSL/TLS**

Secure Socket Layer (SSL) and Transport Layer Security (TLS) are protocols used to encrypt data exchanged between a client, such as a web browser, and a server. Consider SSL/TLS as a wrapper that encrypts various communication protocols, such as HTTP and FTP, to create HTTPS and FTPS. SSL is not commonly used nowadays as TLS has been gradually replacing it.

#### SSL/TLS Workflow

SSL/TLS handshake is performed to encrypt the communication between client and server through the following steps:

1. Client Hello Message: The client sends a hello message to the server; it includes the client TLS version and the cypher suite that the client supports, in addition to random bytes.
2. Server Hello Message: The server responds with a hello message, highlighting its certificate, chosen cypher suite and random bytes.
3. Authentication: The client authenticates the server’s certificate through the certificate authority that issued it. For example, when we visit [Google](https://www.google.com), Google shares its certificate. The received certificate is verified by our browser, which is pre-installed with the certificates of various certificate authorities.
4. Premaster Secret: The client encrypts random bytes with the server’s public key. (The client retrieves the public key from the server’s certificate.)
5. Decryption of Premaster: The server decrypts the premaster with its private key.
6. Session Keys Generated: The client and the server generate session keys based on client random bytes, random server bytes and premaster secret. Both will arrive at the same results; this session key is not transmitted, and encryption and decryption are based on this key.
7. Ready Messages: The client and server send a “finished” message using the session key to indicate that the session is ready for transmission. The client and server are now ready to exchange messages over SSL/TLS encrypted connection.

![Figure showing SSL/TLS handshake](https://tryhackme-images.s3.amazonaws.com/user-uploads/5f04259cf9bf5b57aed2c476/room-content/f1a7e8eaf28b773aab4b5d3ae0f563b6.png)

TLS is a wrapper that encrypts communication of communication protocols. It has port numbers for various protocols, such as 443 for HTTPS and 990 for FTPS.

#### SOCKS5 Protocol

**Technical Overview - SOCKS5**

Socket Secure (SOCKS) is a proxy protocol for data exchange through a delegate server (SOCKS5 proxy). It is used to secure application layer protocols. For example, the Squid server implements the SOCKS5 protocol to transfer data via the HTTP protocol.

**SOCKS5 Workflow**

Consider a scenario when user A wants to connect with client B over the Internet, but a firewall is between them. The following handshake steps are involved:

* **Client Initiation**
  * Client A connects with the SOCKS5 proxy and sends the first byte (0x05) to the proxy where “5” is the SOCKS version.
  * Client A sends a second byte (0x01). One means authentication is supported.
  * Client A sends the third byte (0x00, 0x01, 0x02, or 0x03); these bytes denote the supported authentication methods and can be of variable length.
* **SOCKS5 Proxy Reply**
  * The proxy sends back a second byte, which is the chosen authentication method by the proxy server.
  * After the initiation packet, client A sends the request packet, which includes BHOST & BPORT numbers.
  * The successful session is established between client A and the proxy. The same steps are involved in the association of client B with the proxy.
* **Data Transfer**
  * After successfully associating both clients with a proxy server, both clients can exchange data and share information that will be routed through the proxy server.

![Figure showing client A connecting to a SOCKS5 proxy and using that as a relay to connect to Client B.](https://tryhackme-images.s3.amazonaws.com/user-uploads/5f04259cf9bf5b57aed2c476/room-content/3814e1abc3946c5f256e5b9aa7eff893.png)

**Benefits of SOCKS5**

* In direct communication via the proxy server, hide the internal details from routing over the Internet.
* A proxy acts as a relay server, bypassing Internet censorship based on the client’s IP address.
