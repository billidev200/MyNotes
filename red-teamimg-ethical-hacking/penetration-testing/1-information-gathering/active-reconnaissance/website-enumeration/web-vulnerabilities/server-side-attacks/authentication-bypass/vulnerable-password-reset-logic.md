# Vulnerable Password Reset Logic

## Exploiting Vulnerable Password Reset Logic

**Email-Based Reset**

When a user resets their password, the application sends an email containing a reset link or a token to the user’s registered email address. The user then clicks on this link, which directs them to a page where they can enter a new password and confirm it, or a system will automatically generate a new password for the user. This method relies heavily on the security of the user's email account and the secrecy of the link or token sent.

**Security Question-Based Reset**

This involves the user answering a series of pre-configured security questions they had set up when creating their account. If the answers are correct, the system allows the user to proceed with resetting their password. While this method adds a layer of security by requiring information only the user should know, it can be compromised if an attacker gains access to personally identifiable information (PII), which can sometimes be easily found or guessed.

**SMS-Based Reset**

This functions similarly to email-based reset but uses SMS to deliver a reset code or link directly to the user’s mobile phone. Once the user receives the code, they can enter it on the provided webpage to access the password reset functionality. This method assumes that access to the user's phone is secure, but it can be vulnerable to SIM swapping attacks or intercepts.

Each of these methods has its vulnerabilities:

* **Predictable Tokens**: If the reset tokens used in links or SMS messages are predictable or follow a sequential pattern, attackers might guess or brute-force their way to generate valid reset URLs.
* **Token Expiration Issues**: Tokens that remain valid for too long or do not expire immediately after use provide a window of opportunity for attackers. It’s crucial that tokens expire swiftly to limit this window.
* **Insufficient Validation**: The mechanisms for verifying a user’s identity, like security questions or email-based authentication, might be weak and susceptible to exploitation if the questions are too common or the email account is compromised.
* **Information Disclosure**: Any error message that specifies whether an email address or username is registered can inadvertently help attackers in their enumeration efforts, confirming the existence of accounts.
* **Insecure Transport**: The transmission of reset links or tokens over non-HTTPS connections can expose these critical elements to interception by network eavesdroppers.

### Exploiting Predictable Tokens

```
$token = mt_rand(100, 200);
$query = $conn->prepare("UPDATE users SET reset_token = ? WHERE email = ?");
$query->bind_param("ss", $token, $email);
$query->execute();
```

{% hint style="warning" %}
if the logic is like this we can use burpsuite to bruteforce the token until we get the page of the password reset because the token length is very small
{% endhint %}

<figure><img src="../../../../../../../../.gitbook/assets/645b19f5d5848d004ab9c9e2-1719133559379.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../../../../../../.gitbook/assets/645b19f5d5848d004ab9c9e2-1719134236525.png" alt=""><figcaption></figcaption></figure>

