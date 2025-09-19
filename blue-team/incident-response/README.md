# Incident Response

## Types of Incidents

* **Malware Infections**: Malware is a malicious program that can damage a system, network, or application. The majority of incidents are associated with malware infections.  There are different types of malware, each with a unique potential to cause damage. Malware infections are mostly caused by files that can be text, documents, executables, etc.

<figure><img src="../../.gitbook/assets/6645aa8c024f7893371eb7ac-1718267680505.png" alt="" width="188"><figcaption></figcaption></figure>



* **Security Breaches:** Security Breaches arise when an unauthorized person gets access to confidential data (something we don’t want them to see or have).  Security Breaches are of the utmost importance as many businesses rely on their confidential data, which must only be accessible to authorized personnel.

<figure><img src="../../.gitbook/assets/6645aa8c024f7893371eb7ac-1718267680503.png" alt="" width="375"><figcaption></figcaption></figure>

* **Data Leaks:** Data leaks are incidents in which confidential information of an individual or an organization is exposed to unauthorized entities. Many attackers use data leaks for reputational damage to their victims or use this technique to threaten their victims and get what they need from them. Unlike Security Breaches, data leaks can also be unintentionally caused by human errors or misconfigurations.

<figure><img src="../../.gitbook/assets/6645aa8c024f7893371eb7ac-1718267680577.png" alt="" width="375"><figcaption></figcaption></figure>

* **Insider Attacks:** Incidents from within an organization are known as insider attacks. Think about a disgruntled employee infecting the whole network through a USB on his last day. This is an example of an insider attack. Someone within your organization intentionally initiating an attack comes under this category. These attacks can be hazardous, as an insider always has greater access to resources than an outsider.

<figure><img src="../../.gitbook/assets/6645aa8c024f7893371eb7ac-1718267680502.png" alt="" width="375"><figcaption></figcaption></figure>

* **Denial Of Service Attacks:** Availability is one of the three pillars of cyber security. Defensive security solutions and people constantly find ways to protect information; they ensure that the data is available to the people simultaneously. This is because there is no point in protecting something that is unavailable to us. Denial of Service attacks, or DoS attacks, are incidents where the attacker floods a system/network/application with false requests, eventually making it unavailable to legitimate users. This happens due to the exhaustion of resources available to entertain the requests.

<figure><img src="../../.gitbook/assets/6645aa8c024f7893371eb7ac-1718267680690 (1).png" alt="" width="375"><figcaption></figcaption></figure>

***

## Incident Response Process

| Phase           | Explanation                                                                                                                                                                                                                                                                                      | Example                                                                                                                                                                                                        |
| --------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Preparation     | This is the first phase. The preparation phase includes building the necessary resources to handle an incident. These resources include developing incident response teams, having a proper incident response plan in place, and deploying necessary security solutions to combat the incidents. | Conducting awareness training for employees on phishing emails. Phishing emails are fraudulent emails sent by malicious attackers that can trick you into performing actions that can lead you to an incident. |
| Identification  | The identification phase refers to looking for any abnormal behavior that may indicate an incident. This involves using various security solutions and techniques to monitor abnormal events.                                                                                                    | The security team notices a huge amount of data being sent out from one of the hosts. Upon analysis, it was found to be compromised after a malicious file was downloaded from a phishing email attachment.    |
| Containment     | Once an incident has been identified, the next step should be to contain it. This means minimizing the impact of the attack. This is usually done by isolating the victim machine, disabling the compromised user accounts, etc.                                                                 | The Security team isolates the host from the network to minimize the impact and not allow the attacker to jump to other systems, leveraging the compromised host.                                              |
| Eradication     | This phase, as its name suggests, involves removing the threat from the attacked environment. The threat may be of any kind. The eradication phase will ensure the subject environment is clean, and now we can move to the recovery phase.                                                      | A deep malware scan was executed on the system to remove the malicious software from the host.                                                                                                                 |
| Recovery        | The recovery phase is very important in this chain. It involves recovering the affected systems from backup or rebuilding them. The recovered systems are then tested and are ready to use.                                                                                                      | The compromised host was re-configured, and the exfiltrated data was restored from the backup.                                                                                                                 |
| Lessons Learned | This is also an important part of the incident response lifecycle. Gaps in the detection and analysis of the incident are identified and documented, helping to improve the overall process in future incidents.                                                                                 | Conducting a post-incident review meeting to analyze the incident's root cause and improve the security to prevent future attacks.                                                                             |

**SANS**

<figure><img src="../../.gitbook/assets/6645aa8c024f7893371eb7ac-1718265520999.png" alt="" width="375"><figcaption></figcaption></figure>

**NIST**

<figure><img src="../../.gitbook/assets/6645aa8c024f7893371eb7ac-1718268206803.png" alt=""><figcaption></figcaption></figure>

**Comperasion**

<figure><img src="../../.gitbook/assets/6645aa8c024f7893371eb7ac-1723217056943.png" alt=""><figcaption></figcaption></figure>

## Playbooks

Following is an example of a **Playbook** for an incident: Phishing Email

1. Notify all the stakeholders of the phishing email incident
2. Determine if the email was malicious by conducting header and body analysis of the email
3. Look for any attachments with the email and analyze them
4. Determine if anybody opened the attachments
5. Isolate the infected systems from the network
6. Block the email sender
