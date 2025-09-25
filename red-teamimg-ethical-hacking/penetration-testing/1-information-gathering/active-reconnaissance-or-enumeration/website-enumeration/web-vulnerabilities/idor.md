---
description: Insecure direct object references
---

# IDOR

It’s a type of **access control vulnerability** where an application exposes internal implementation details (like file names, database IDs, or keys) and fails to properly enforce authorization checks.

👉 In simple terms:\
An attacker can directly manipulate an identifier (like a user ID or file ID) in the URL, request body, or API call to access or modify data they shouldn’t have access to.

## Example 1

A web app shows a user’s invoice:

```url
https://example.com/invoice?id=123
```

If the app only checks that the ID exists but **not** that it belongs to the logged-in user, an attacker could change it:

```
https://example.com/invoice?id=124
```

and now see another user’s invoice.

## Example 2

For example, let's say we're logging into our bank account, and after correctly authenticating ourselves, we get taken to a URL like this `https://bank.thm/account?id=111111`. On that page, we can see all our important bank details, and a user would do whatever they need to do and move along their way, thinking nothing is wrong.

<figure><img src="../../../../../../.gitbook/assets/0ddb5676eebdb367bff750717268b82b.png" alt="" width="563"><figcaption></figcaption></figure>

There is, however, a potentially huge problem here, anyone may be able to change the `id` parameter to something else like `222222`, and if the site is incorrectly configured, then he would have access to someone else's bank information.

<figure><img src="../../../../../../.gitbook/assets/42a83d8c119295a79dfcab36b7e4d105.png" alt="" width="563"><figcaption></figcaption></figure>

