# Mass Assignment

Mass assignment reflects a scenario where client-side data is automatically bound with server-side objects or class variables. However, hackers exploit the feature by first understanding the application's business logic and sending specially crafted data to the server, acquiring administrative access or inserting tampered data. This functionality is widely exploited in the latest frameworks like Laravel, Code Ignitor etc.

Consider a user's profiles dashboard where users can update their profile like associated email, name, address etc. The username of the user is a read-only attribute and cannot be changed; however, a malicious actor can edit the username and submit the form. If necessary filtration is not enabled on the server side (model), it will simply insert/update the data in the database.

<figure><img src="../../../../../../../.gitbook/assets/31d541b9eb6d7f67dec8fdb60d07f8af.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../../../../../.gitbook/assets/bfb2c99ce2c72649953967a629cbcc39.png" alt=""><figcaption></figcaption></figure>
