# Insecure Deserialization

{% embed url="https://www.youtube.com/watch?v=aC-nCEOVdKE" %}

1. **Insecure Deserialization** occurs when an application **accepts serialized data from the client, deserializes it, and trusts its content**, allowing an attacker to manipulate the data to perform unintended actions.
   * Example: If the server expects a serialized object like `{"requestId":123,"price":50}` and you change `price` in the serialized data, and the server blindly trusts it, that’s **Insecure Deserialization**.
2. **IDOR (Insecure Direct Object Reference)** happens when **you change identifiers or references in a request** to access or modify something you shouldn’t.
   * Example: If you change `trasherRequestId=10` to `trasherRequestId=11` to update someone else’s request, that’s **IDOR**.

✅ Key difference:

* If you **change the price** field in a request for your own object, it’s usually considered **Insecure Deserialization** (or a business logic flaw) if the server blindly trusts client input.
* If you **change the ID to modify someone else’s object**, that’s **IDOR**.

Simply, insecure deserialization occurs when data from an untrusted party (I.e. a hacker) gets executed because there is no filtering or input validation; the system assumes that the data is trustworthy and will execute it no holds barred.
