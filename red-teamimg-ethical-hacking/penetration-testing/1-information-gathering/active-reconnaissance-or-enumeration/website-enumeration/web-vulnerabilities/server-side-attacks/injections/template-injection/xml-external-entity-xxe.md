# XML External Entity (XXE)

<figure><img src="../../../../../../../../../.gitbook/assets/XXE_600x315.png" alt=""><figcaption></figcaption></figure>

An XML External Entity (XXE) attack is a vulnerability that abuses features of XML parsers/data. It often allows an attacker to interact with any backend or external systems that the application itself can access and can allow the attacker to read the file on that system. They can also cause Denial of Service (DoS) attack or could use XXE to perform Server-Side Request Forgery (SSRF) inducing the web application to make requests to other applications. XXE may even enable port scanning and lead to remote code execution.\
\
There are two types of XXE attacks: in-band and out-of-band (OOB-XXE).\
1\) An in-band XXE attack is the one in which the attacker can receive an immediate response to the XXE payload.

{% embed url="https://www.youtube.com/watch?v=gjm6VHZa_8s" %}

2\) out-of-band XXE attacks (also called blind XXE), there is no immediate response from the web application and attacker has to reflect the output of their XXE payload to some other file or their own server.
