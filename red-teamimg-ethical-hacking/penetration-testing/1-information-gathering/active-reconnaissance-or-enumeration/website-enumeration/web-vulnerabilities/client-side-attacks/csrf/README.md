---
description: >-
  Cross-site request forgery (also known as CSRF) is a web security
  vulnerability that allows an attacker to induce users to perform actions that
  they do not intend to perform. It allows an attacker to
---

# CSRF

{% embed url="https://portswigger.net/web-security/csrf" %}

## Effects of CSRF

Understanding CSRF's impact is crucial for keeping online activities secure. Although CSRF attacks don't directly expose user data, they can still cause harm by changing passwords and email addresses or making financial transactions. The risks associated with CSRF include:

* Unauthorised Access: Attackers can access and control a user's actions, putting them at risk of losing money, damaging their reputation, and facing legal consequences.
* Exploiting Trust: CSRF exploits the trust websites put in their users, undermining the sense of security in online browsing.
* Stealthy Exploitation: CSRF works quietly, using standard browser behaviour without needing advanced malware. Users might be unaware of the attack, making them susceptible to repeated exploitation.

## Types of CSRF Attack

<figure><img src="../../../../../../../../.gitbook/assets/Screenshot 2025-11-24 211245.png" alt=""><figcaption></figcaption></figure>
