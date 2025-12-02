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

* **Unauthorised Access:** Attackers can access and control a user's actions, putting them at risk of losing money, damaging their reputation, and facing legal consequences.
* **Exploiting Trust:** CSRF exploits the trust websites put in their users, undermining the sense of security in online browsing.
* **Stealthy Exploitation:** CSRF works quietly, using standard browser behaviour without needing advanced malware. Users might be unaware of the attack, making them susceptible to repeated exploitation.

{% hint style="info" %}
Can happen anywere even password change,delete account , change email.Besicly we send the same rqeust for example post to update  email but becuase there is not csrf token anyone can send  reqeust if it has the cookie/token or make  ink when someone press it the request it sends.

Also if there is csrf token we can try removing it and see if work
{% endhint %}



{% embed url="https://www.youtube.com/watch?t=91s&v=wYazaHJ3l0E" %}

## Types of CSRF Attack

<figure><img src="../../../../../../../../.gitbook/assets/Screenshot 2025-11-24 211245.png" alt=""><figcaption></figcaption></figure>

**Flash-based CSRF**

The term "Flash-based CSRF" describes the technique of conducting a CSRF attack by taking advantage of flaws in Adobe Flash Player components. Internet applications with features like interactive content, video streaming, and intricate animations![flash based csrf](https://tryhackme-images.s3.amazonaws.com/user-uploads/62a7685ca6e7ce005d3f3afe/room-content/328966e16f936388539965b9bf110581.svg) have been made possible with Flash. But over time, security flaws in Flash, particularly those that can be used to launch CSRF attacks, have become a major source of worry. As HTML5 technology advanced and security flaws multiplied, official support for Adobe Flash Player ceased on [December 31, 2020](https://www.adobe.com/products/flashplayer/end-of-life.html).

Even though Flash is no longer supported, a talk about Flash-based cross-site request forgery threats is instructive, particularly for legacy systems that still rely on antiquated technologies. A malicious Flash file (.swf) posted on the attacker's website would typically send unauthorised requests to other websites to carry out Flash-based CSRF attacks.
