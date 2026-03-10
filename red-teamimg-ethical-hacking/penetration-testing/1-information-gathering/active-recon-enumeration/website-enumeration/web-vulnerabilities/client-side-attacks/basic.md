# Basic

## Clickjacking

* Attacker loads the target site inside an invisible `<iframe>`
* Tricks the victim into clicking hidden buttons
* Used for forced likes, financial actions, account changes

## **Clipboard Injection**

* Malicious page replaces content in the user’s clipboard
* E.g., swapping a crypto wallet address

## **Browser Autofill Attack**

* Fake or hidden fields harvest autofill data
* Browser fills name, email, phone, address automatically

## **Formjacking**

* Malicious JS injected into payment pages
* Steals credit card data (Magecart attacks)

## Redirection Attack

{% embed url="https://www.youtube.com/watch?v=4Jk_I-cw4WE" %}

A redirection attack happens when an attacker manipulates a website or vulnerable parameter to **redirect the victim to another page**, usually a malicious one

```
https://example.com/login?redirect=https://evil.com/phishing
```
