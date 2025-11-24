# Authentication Bypass

* **Brute force attacks:** If a web application uses usernames and passwords, an attacker can try to launch brute force attacks that allow them to guess the username and passwords using multiple authentication attempts.&#x20;
* **Use of weak credentials:** Web applications should set strong password policies. If applications allow users to set passwords such as "password1" or common passwords, an attacker can easily guess them and access user accounts.
* **Weak Session Cookies:** Session cookies are how the server keeps track of users. If session cookies contain predictable values, attackers can set their own session cookies and access users' accounts.
* **Logic Flaw:** Sometimes authentication processes contain logic flaws. A logic flaw is when the typical logical path of an application is either bypassed,
* **Cookie Tampering:**&#x45;xamining and editing the cookies set by the web server during your online session can have multiple outcomes, such as unauthenticated access, access to another user's account, or elevated privileges.it can happen if stole a cookie from someone and use to login or if it not encoded hashed and has exposed parameters be vulnerable to IDOR.

There can be various mitigation for broken authentication mechanisms depending on the exact flaw:

* To avoid password-guessing attacks, ensure the application enforces a strong password policy.&#x20;
* To avoid brute force attacks, ensure that the application enforces an automatic lockout after a certain number of attempts. This would prevent an attacker from launching more brute-force attacks.
* Implement Multi-Factor Authentication. If a user has multiple authentication methods, for example, using a username and password and receiving a code on their mobile device, it would be difficult for an attacker to get both the password and the code to access the account.

```bash
ffuf -w /usr/share/wordlists/SecLists/Usernames/Names/names.txt -X POST -d "username=FUZZ&email=x&password=x&cpassword=x" -H "Content-Type: application/x-www-form-urlencoded" -u http://10.10.134.143/customers/signup -mr "username already exists"
```

