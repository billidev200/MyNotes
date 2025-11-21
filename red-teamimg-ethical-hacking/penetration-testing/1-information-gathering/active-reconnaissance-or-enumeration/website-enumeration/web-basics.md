# Web Basics

## Uniform Resource Locator (URL)

A Uniform Resource Locator (URL) is a web address that lets you access all kinds of online content—whether it’s a webpage, a video, a photo, or other media. It guides your browser to the right place on the Internet.

<figure><img src="../../../../../.gitbook/assets/34ad66d8b90aaaa35f9536d3b152ea97.png" alt=""><figcaption></figcaption></figure>

**Scheme**

The **scheme** is the protocol used to access the website. The most common are **HTTP** (HyperText Transfer Protocol) and **HTTPS** (Hypertext Transfer Protocol Secure). HTTPS is more secure because it encrypts the connection, which is why browsers and cyber security experts recommend it. Websites often enforce HTTPS for added protection.

**User**

Some URLs can include a user’s login details (usually a username) for sites that require authentication. This happens mostly in URLs that need credentials to access certain resources. However, it’s rare nowadays because putting login details in the URL isn’t very safe—it can expose sensitive information, which is a security risk.

**Host/Domain**

The **host** or **domain** is the most important part of the URL because it tells you which website you’re accessing. Every domain name has to be unique and is registered through domain registrars. From a security standpoint, look for domain names that appear almost like real ones but have small differences (this is called **typosquatting**). These fake domains are often used in phishing attacks to trick people into giving up sensitive info.

**Port**

The **port number** helps direct your browser to the right service on the web server. It’s like telling the server which doorway to use for communication. Port numbers range from 1 to 65,535, but the most common are **80** for HTTP and **443** for HTTPS.

**Path**

The **path** points to the specific file or page on the server that you’re trying to access. It’s like a roadmap that shows the browser where to go. Websites need to secure these paths to make sure only authorised users can access sensitive resources.

**Query String**

The **query string** is the part of the URL that starts with a question mark (?). It’s often used for things like search terms or form inputs. Since users can modify these query strings, it’s important to handle them securely to prevent attacks like **injections**, where malicious code could be added.

**Fragment**

The **fragment** starts with a hash symbol (#) and helps point to a specific section of a webpage—like jumping directly to a particular heading or table. Users can modify this too, so like with query strings, it’s important to check and clean up any data here to avoid issues like injection attacks.

### URL Path

The **URL path** tells the server where to find the resource the user is asking for. For instance, in the URL `https://tryhackme.com/api/users/123`, the path `/api/users/123` identifies a specific user.

Attackers often try to manipulate the URL path to exploit vulnerabilities, so it’s crucial to:

* Validate the URL path to prevent unauthorised access
* Sanitise the path to avoid injection attacks
* Protect sensitive data by conducting privacy and risk assessments

## HTTP Methods - Status Codes

### HTTP header

<figure><img src="../../../../../.gitbook/assets/5f04259cf9bf5b57aed2c476-1730445201524.png" alt=""><figcaption></figcaption></figure>

### Status Codes

<figure><img src="../../../../../.gitbook/assets/HttpStatusCode (1).png" alt=""><figcaption></figcaption></figure>

### Status Line

The first line in every HTTP response is called the **Status Line**. It gives you three key pieces of info:

1. **HTTP Version**: This tells you which version of HTTP is being used.
2. **Status Code**: A three-digit number showing the outcome of your request.
3. **Reason Phrase**: A short message explaining the status code in human-readable terms.

Since we already covered HTTP Versions in Task 5, let’s focus on the **Status Codes** and **Reason Phrases** here.

***

The **HTTP method** tells the server what action the user wants to perform on the resource identified by the URL path. Here are some of the most common methods and their possible security issue:

GET\
Used to fetch data from the server without making any changes. Reminder! Make sure you’re only exposing data the user is allowed to see. Avoid putting sensitive info like tokens or passwords in GET requests since they can show up as plaintext.

**POST**\
Sends data to the server, usually to create or update something. Reminder! Always validate and clean the input to avoid attacks like SQL injection or XSS.

PUT\
Replaces or updates something on the server. Reminder! Make sure the user is authorised to make changes before accepting the request.

**DELETE**\
Removes something from the server. Reminder! Just like with PUT, make sure only authorised users can delete resources.

Besides these common methods, there are a few others used in specific cases:

PATCH\
Updates part of a resource. It’s useful for making small changes without replacing the whole thing, but always validate the data to avoid inconsistencies.

HEAD\
Works like GET but only retrieves headers, not the full content. It’s handy for checking metadata without downloading the full response.

OPTIONS\
Tells you what methods are available for a specific resource, helping clients understand what they can do with the server.

TRACE\
Similar to OPTIONS, it shows which methods are allowed, often for debugging. Many servers disable it for security reasons.

CONNECT\
Used to create a secure connection, like for HTTPS. It’s not as common but is critical for encrypted communication.

***

### HTTP Versions

The **HTTP version** shows the protocol version used to communicate between the client and server. Here’s a quick rundown of the most common ones:

**HTTP/0.9** (1991)\
The first version, only supported GET requests.

**HTTP/1.0** (1996)\
Added headers and better support for different types of content, improving caching.

**HTTP/1.1** (1997)\
Brought persistent connections, chunked transfer encoding, and better caching. It’s still widely used today.

**HTTP/2** (2015)\
Introduced features like multiplexing, header compression, and prioritisation for faster performance.

**HTTP/3** (2022)\
Built on HTTP/2, but uses a new protocol (QUIC) for quicker and more secure connections.

Although HTTP/2 and HTTP/3 offer better speed and security, many systems still use **HTTP/1.1** because it’s well-supported and works with most existing setups. However, upgrading to HTTP/2 or HTTP/3 can provide significant performance and security improvements as more systems adopt them.

***

### Request Headers

Request Headers allow extra information to be conveyed to the web server about the request. Some common headers are as follows:

**Common Request Headers**

| Request Header | Example                                                                          | Description                                                                              |
| -------------- | -------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------- |
| Host           | `Host: tryhackme.com`                                                            | Specifies the name of the web server the request is for.                                 |
| User-Agent     | `User-Agent: Mozilla/5.0`                                                        | Shares information about the web browser the request is coming from.                     |
| Referer        | `Referer: https://www.google.com/`                                               | Indicates the URL from which the request came from.                                      |
| Cookie         | `Cookie: user_type=student; room=introtowebapplication; room_status=in_progress` | Information the web server previously asked the web browser to store is held in cookies. |
| Content-Type   | `Content-Type: application/json`                                                 | Describes what type or format of data is in the request.                                 |

| Header                                        | Example                                              | Description                                                                   |
| --------------------------------------------- | ---------------------------------------------------- | ----------------------------------------------------------------------------- |
| **General Headers**                           |                                                      |                                                                               |
| Cache-Control                                 | `Cache-Control: no-cache`                            | Directives for caching mechanisms in requests/responses.                      |
| Connection                                    | `Connection: keep-alive`                             | Controls whether the network connection stays open after the request.         |
| Date                                          | `Date: Tue, 15 Nov 1994 08:12:31 GMT`                | The date/time the request was sent.                                           |
| Pragma                                        | `Pragma: no-cache`                                   | Legacy HTTP/1.0 header, used for backward compatibility with caching.         |
| Trailer                                       | `Trailer: Expires`                                   | Indicates which headers will be sent in the trailer after the message body.   |
| Transfer-Encoding                             | `Transfer-Encoding: chunked`                         | Specifies the encoding form of the request body.                              |
| Upgrade                                       | `Upgrade: h2c`                                       | Asks the server to switch protocols.                                          |
| Via                                           | `Via: 1.1 proxy`                                     | Shows intermediate proxies/servers through which the request passed.          |
| Warning                                       | `Warning: 199 Miscellaneous warning`                 | Extra information about possible problems with the request.                   |
| **Request-Specific Headers**                  |                                                      |                                                                               |
| Accept                                        | `Accept: text/html,application/json`                 | Lists media types the client can handle.                                      |
| Accept-Charset                                | `Accept-Charset: utf-8`                              | Lists character sets the client can handle.                                   |
| Accept-Encoding                               | `Accept-Encoding: gzip, deflate, br`                 | Lists content encodings the client supports.                                  |
| Accept-Language                               | `Accept-Language: en-US,en;q=0.5`                    | Lists natural languages the client prefers.                                   |
| Authorization                                 | `Authorization: Basic QWxhZGRpbjpvcGVuIHNlc2FtZQ==`  | Credentials for authenticating the client to the server.                      |
| Cookie                                        | `Cookie: sessionid=abc123; theme=dark`               | Stores data previously set by the server for session/state.                   |
| Expect                                        | `Expect: 100-continue`                               | Indicates expectations the client requires from the server.                   |
| From                                          | `From: user@example.com`                             | Email address of the user making the request.                                 |
| Host                                          | `Host: www.example.com`                              | Specifies the host and port of the requested resource.                        |
| If-Match                                      | `If-Match: "etagvalue"`                              | Makes request conditional on resource matching a specific ETag.               |
| If-Modified-Since                             | `If-Modified-Since: Sat, 29 Oct 1994 19:43:31 GMT`   | Sends request only if resource has been modified since given date.            |
| If-None-Match                                 | `If-None-Match: "etagvalue"`                         | Sends request only if resource ETag does _not_ match.                         |
| If-Range                                      | `If-Range: "etagvalue"`                              | Requests partial content if entity matches ETag/date, otherwise full.         |
| If-Unmodified-Since                           | `If-Unmodified-Since: Sat, 29 Oct 1994 19:43:31 GMT` | Only performs request if resource not modified since date.                    |
| Max-Forwards                                  | `Max-Forwards: 10`                                   | Limits how many proxies/gateways a request can travel through.                |
| Proxy-Authorization                           | `Proxy-Authorization: Basic abc123`                  | Credentials for authenticating with a proxy.                                  |
| Range                                         | `Range: bytes=500-999`                               | Requests part of a resource (used for resumable downloads).                   |
| Referer                                       | `Referer: https://google.com/`                       | The previous page the client came from.                                       |
| TE                                            | `TE: trailers, deflate`                              | Specifies transfer encodings the client is willing to accept.                 |
| User-Agent                                    | `User-Agent: Mozilla/5.0`                            | Identifies the client software (browser, bot, tool).                          |
| **Entity Headers (for requests with a body)** |                                                      |                                                                               |
| Content-Encoding                              | `Content-Encoding: gzip`                             | Encoding applied to the body (compression).                                   |
| Content-Language                              | `Content-Language: en`                               | Natural language of the body data.                                            |
| Content-Length                                | `Content-Length: 1234`                               | Size of the body in bytes.                                                    |
| Content-Location                              | `Content-Location: /index.htm`                       | Location of the body data.                                                    |
| Content-MD5 _(deprecated)_                    | `Content-MD5: Q2hlY2sgSW50ZWdyaXR5IQ==`              | Base64-encoded MD5 checksum of body.                                          |
| Content-Range                                 | `Content-Range: bytes 21010-47021/47022`             | Position of partial content within full body.                                 |
| Content-Type                                  | `Content-Type: application/json`                     | Media type of the body (e.g., JSON, HTML, XML).                               |
| **Security / Control Headers**                |                                                      |                                                                               |
| Origin                                        | `Origin: https://example.com`                        | Specifies the origin of a cross-site request (CORS).                          |
| Sec-Fetch-Site                                | `Sec-Fetch-Site: same-origin`                        | Part of Fetch Metadata to prevent CSRF and cross-origin leaks.                |
| Sec-Fetch-Mode                                | `Sec-Fetch-Mode: cors`                               | Indicates the request mode (cors, navigate, no-cors, etc.).                   |
| Sec-Fetch-User                                | `Sec-Fetch-User: ?1`                                 | Indicates if request was user-initiated (e.g., a click).                      |
| Sec-Fetch-Dest                                | `Sec-Fetch-Dest: document`                           | Describes the destination of the request.                                     |
| DNT                                           | `DNT: 1`                                             | Indicates the user’s Do Not Track preference.                                 |
| Upgrade-Insecure-Requests                     | `Upgrade-Insecure-Requests: 1`                       | Instructs server to send HTTPS instead of HTTP if available.                  |
| X-Requested-With                              | `X-Requested-With: XMLHttpRequest`                   | Commonly used by AJAX calls to identify request type.                         |
| **Custom / Non-Standard (Vendor-Specific)**   |                                                      |                                                                               |
| X-Forwarded-For                               | `X-Forwarded-For: 192.0.2.43`                        | Shows the original client IP when request passed through proxy/load balancer. |
| X-Forwarded-Host                              | `X-Forwarded-Host: original.example.com`             | Shows the original host requested by client.                                  |
| X-Forwarded-Proto                             | `X-Forwarded-Proto: https`                           | Indicates original protocol (http/https).                                     |
| Front-End-Https                               | `Front-End-Https: on`                                | Microsoft header for indicating HTTPS offloading.                             |
| X-Real-IP                                     | `X-Real-IP: 203.0.113.195`                           | Passes the real client IP.                                                    |
| X-Csrf-Token                                  | `X-Csrf-Token: abc123`                               | Token to prevent CSRF attacks.                                                |
| X-Api-Key                                     | `X-Api-Key: 123456`                                  | Used for API authentication.                                                  |
| X-Frame-Options _(response usually)_          | `X-Frame-Options: DENY`                              | Prevents embedding of page in iframes.                                        |
| Request-ID / X-Request-ID                     | `X-Request-ID: abc-123`                              | <p>Correlates logs across </p><p>distributed systems.</p>                     |

### Request Body

In HTTP requests such as POST and PUT, where data is sent to the web server as opposed to requested from the web server, the data is located inside the HTTP Request Body. The formatting of the data can take many forms, but some common ones are `URL Encoded`, `Form Data`, `JSON`, or `XML`.

*   URL Encoded (application/x-www-form-urlencoded)\
    A format where data is structured in pairs of key and value where (`key=value`). Multiple pairs are separated by an (`&`) symbol, such as `key1=value1&key2=value2`. Special characters are percent-encoded.\
    \
    &#xNAN;_&#x45;xample_<br>

    ```http
    POST /profile HTTP/1.1
    Host: tryhackme.com
    User-Agent: Mozilla/5.0
    Content-Type: application/x-www-form-urlencoded
    Content-Length: 33

    name=Aleksandra&age=27&country=US
    ```
*   Form Data (multipart/form-data)\
    Allows multiple data blocks to be sent where each block is separated by a boundary string. The boundary string is the defined header of the request itself. This type of formatting can be used to send binary data, such as when uploading files or images to a web server.\
    \
    &#xNAN;_&#x45;xample_<br>

    ```http
    POST /upload HTTP/1.1
    Host: tryhackme.com
    User-Agent: Mozilla/5.0
    Content-Type: multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW

    ----WebKitFormBoundary7MA4YWxkTrZu0gW
    Content-Disposition: form-data; name="username"

    aleksandra
    ----WebKitFormBoundary7MA4YWxkTrZu0gW
    Content-Disposition: form-data; name="profile_pic"; filename="aleksandra.jpg"
    Content-Type: image/jpeg

    [Binary Data Here representing the image]
    ----WebKitFormBoundary7MA4YWxkTrZu0gW--
    ```
*   JSON (application/json)\
    In this format, the data can be sent using the JSON (JavaScript Object Notation) structure. Data is formatted in pairs of name : value. Multiple pairs are separated by commas, all contained within curly braces { }.\
    \
    &#xNAN;_&#x45;xample_<br>

    ```http
    POST /api/user HTTP/1.1
    Host: tryhackme.com
    User-Agent: Mozilla/5.0
    Content-Type: application/json
    Content-Length: 62

    {
        "name": "Aleksandra",
        "age": 27,
        "country": "US"
    }
    ```
*   XML (application/xml)\
    In XML formatting, data is structured inside labels called tags, which have an opening and closing. These labels can be nested within each other. You can see in the example below the opening and closing of the tags to send details about a user called Aleksandra.\
    \
    &#xNAN;_&#x45;xample_<br>

    ```http
    POST /api/user HTTP/1.1
    Host: tryhackme.com
    User-Agent: Mozilla/5.0
    Content-Type: application/xml
    Content-Length: 124

    <user>
        <name>Aleksandra</name>
        <age>27</age>
        <country>US</country>
    </user>
    ```

### Response Headers

| Header                                          | Example                                          | Description                                                                                                       |
| ----------------------------------------------- | ------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------- |
| **Required by HTTP/1.1 (RFC 7230, RFC 7231)**   |                                                  |                                                                                                                   |
| `Date`                                          | `Date: Tue, 25 Sep 2025 10:00:00 GMT`            | MUST be sent in all responses (unless the server doesn’t have a clock). Provides the date/time of the message.    |
| `Server` _(recommended, not strictly required)_ | `Server: Apache/2.4.1 (Unix)`                    | Identifies the software handling the request (can be omitted for security reasons).                               |
| `Content-Length` OR `Transfer-Encoding`         | `Content-Length: 348Transfer-Encoding: chunked`  | One of these is required if there is a body. They tell the client how much data to expect (or that it’s chunked). |
| `Content-Type`                                  | `Content-Type: text/html; charset=UTF-8`         | Required when there is a message body, so the client knows how to interpret it.                                   |
| **Conditional / Contextual**                    |                                                  |                                                                                                                   |
| `Location`                                      | `Location: https://example.com/newpage`          | Required in **3xx redirects**. Specifies the new URL to fetch.                                                    |
| `Allow`                                         | `Allow: GET, POST, HEAD`                         | Required in **405 Method Not Allowed** responses, listing permitted methods.                                      |
| `WWW-Authenticate`                              | `WWW-Authenticate: Basic realm="Login Required"` | Required in **401 Unauthorized** responses, tells client how to authenticate.                                     |
| `Proxy-Authenticate`                            | `Proxy-Authenticate: Basic realm="Proxy Login"`  | Required in **407 Proxy Authentication Required** responses.                                                      |

{% hint style="warning" %}
Set-Cookie HTTP response header to ensure they are only transmitted over HTTPS: **Secure**
{% endhint %}

{% hint style="warning" %}
Set-Cookie HTTP response header to prevent them from being accessed via JavaScript: HttpOnly
{% endhint %}

Some response headers are crucial for making sure the HTTP response works properly. They provide essential info that both the client and server need to process everything correctly. Here are a few important ones:

* **Date**:\
  Example: `Date: Fri, 23 Aug 2024 10:43:21 GMT`\
  This header shows the exact date and time when the response was generated by the server.
* **Content-Type**:\
  Example: `Content-Type: text/html; charset=utf-8`\
  It tells the client what kind of content it’s getting, like whether it’s HTML, JSON, or something else. It also includes the character set (like UTF-8) to help the browser display it properly.
* **Server**:\
  Example: `Server: nginx`\
  This header shows what kind of server software is handling the request. It’s good for debugging, but it can also reveal server information that might be useful for attackers, so many people remove or obscure this one.

#### Other Common Response Headers

Besides the essential ones, there are other common headers that give additional instructions to the client or browser and help control how the response should be handled.

* **Set-Cookie**:\
  Example: `Set-Cookie: sessionId=38af1337es7a8`\
  This one sends cookies from the server to the client, which the client then stores and sends back with future requests. To keep things secure, make sure cookies are set with the `HttpOnly` flag (so they can’t be accessed by JavaScript) and the `Secure` flag (so they’re only sent over HTTPS).
* **Cache-Control**:\
  Example: `Cache-Control: max-age=600`\
  This header tells the client how long it can cache the response before checking with the server again. It can also prevent sensitive info from being cached if needed (using `no-cache`).
* **Location**:\
  Example: `Location: /index.html`\
  This one’s used in redirection (3xx) responses. It tells the client where to go next if the resource has moved. If users can modify this header during requests, be careful to validate and sanitise it—otherwise, you could end up with open redirect vulnerabilities, where attackers can redirect users to harmful sites.

#### Response Body

The **HTTP response body** is where the actual data lives—things like HTML, JSON, images, etc., that the server sends back to the client. To prevent **injection attacks** like Cross-Site Scripting (XSS), always sanitise and escape any data (especially user-generated content) before including it in the response.

### Security Headers

HTTP Security Headers help improve the overall security of the web application by providing mitigations against attacks like Cross-Site Scripting (XSS), clickjacking, and others. We will now dig deeper into the following security headers:

* Content-Security-Policy (CSP)
* Strict-Transport-Security (HSTS)
* X-Content-Type-Options
* Referrer-Policy

#### Content-Security-Policy (CSP)

A CSP header is an additional security layer that can help mitigate against common attacks like Cross-Site Scripting (XSS). Malicious code could be hosted on a separate website or domain and injected into the vulnerable website. A CSP provides a way for administrators to say what domains or sources are considered safe and provides a layer of mitigation to such attacks.

Within the header itself, you may see properties such as `default-src` or `script-src` defined and many more. Each of these give an option to an administrator to define at various levels of granularity, what domains are allowed for what type of content. The use of self is a special keyword that reflects the same domain on which the website is hosted.

Looking at an example CSP header:

`Content-Security-Policy: default-src 'self'; script-src 'self' https://cdn.tryhackme.com; style-src 'self'`

We see the use of:

* default-src\
  \- which specifies the default policy of self, which means only the current website.
* script-src\
  \- which specifics the policy for where scripts can be loaded from, which is self along with scripts hosted on `https://cdn.tryhackme.com`
* style-src\
  \- which specifies the policy for where style CSS style sheets can be loaded from the current website (self)

#### Strict-Transport-Security (HSTS)

The HSTS header ensures that web browsers will always connect over HTTPS. Let's look at an example of HSTS:

`Strict-Transport-Security: max-age=63072000; includeSubDomains; preload`\
Here’s a breakdown of the example HSTS header by directive:

* max-age\
  \- This is the expiry time in seconds for this setting
* includeSubDomains\
  \- An optional setting that instructs the browser to also apply this setting to all subdomains.
* preload\
  \- This optional setting allows the website to be included in preload lists. Browsers can use preload lists to enforce HSTS before even having their first visit to a website.

#### X-Content-Type-Options

The X-Content-Type-Options header can be used to instruct browsers not to guess the MIME time of a resource but only use the Content-Type header. Here’s an example:

`X-Content-Type-Options: nosniff`

Here’s a breakdown of the X-Content-Type-Options header by directives:

* nosniff\
  \- This directive instructs the browser not to sniff or guess the MIME type.

#### Referrer-Policy

This header controls the amount of information sent to the destination web server when a user is redirected from the source web server, such as when they click a hyperlink. The header is available to allow a web administrator to control what information is shared.  Here are some examples of Referrer-Policy:

* `Referrer-Policy: no-referrer`
* `Referrer-Policy: same-origin`
* `Referrer-Policy: strict-origin`
* `Referrer-Policy: strict-origin-when-cross-origin`

Here’s a breakdown of the Referrer-Policy header by directives:

* no-referrer\
  \- This completely disables any information being sent about the referrer
* same-origin\
  \- This policy will only send referrer information when the destination is part of the same origin. This is helpful when you want referrer information passed when hyperlinks are within the same website but not outside to external websites.
* strict-origin\
  \- This policy only sends the referrer as the origin when the protocol stays the same. So, a referrer is sent when an HTTPS connection goes to another HTTPS connection.
* strict-origin-when-cross-origin\
  \- This is similar to strict-origin except for same-origin requests, where it sends the full URL path in the origin header.

| Header                                           | Example                                                                                                  | Purpose                                                                                                         |
| ------------------------------------------------ | -------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------- |
| **Content Security**                             |                                                                                                          |                                                                                                                 |
| `Content-Security-Policy` (CSP)                  | `Content-Security-Policy: default-src 'self'; script-src 'self' cdn.example.com`                         | Controls which sources (scripts, styles, images, etc.) can be loaded. Helps prevent **XSS** and data injection. |
| `Content-Security-Policy-Report-Only`            | `Content-Security-Policy-Report-Only: default-src 'self'`                                                | Same as CSP, but only reports violations (does not enforce).                                                    |
| **Transport Security**                           |                                                                                                          |                                                                                                                 |
| `Strict-Transport-Security` (HSTS)               | `Strict-Transport-Security: max-age=31536000; includeSubDomains; preload`                                | Forces the browser to only use HTTPS for future requests. Prevents **SSL stripping attacks**.                   |
| `Upgrade-Insecure-Requests`                      | `Upgrade-Insecure-Requests: 1`                                                                           | Tells browsers to convert `http://` requests into `https://`.                                                   |
| **Clickjacking Protection**                      |                                                                                                          |                                                                                                                 |
| `X-Frame-Options`                                | `X-Frame-Options: DENY`                                                                                  | Prevents page from being embedded in iframes (mitigates **clickjacking**). Replaced by CSP `frame-ancestors`.   |
| **Cross-Site Scripting (XSS) Protection**        |                                                                                                          |                                                                                                                 |
| `X-XSS-Protection` _(deprecated)_                | `X-XSS-Protection: 1; mode=block`                                                                        | Enabled old browser XSS filters. Modern browsers ignore it.                                                     |
| **MIME Type Sniffing**                           |                                                                                                          |                                                                                                                 |
| `X-Content-Type-Options`                         | `X-Content-Type-Options: nosniff`                                                                        | Prevents browsers from MIME-sniffing (guessing file types). Helps stop **drive-by download attacks**.           |
| **Cross-Origin Resource Sharing (CORS)**         |                                                                                                          |                                                                                                                 |
| `Access-Control-Allow-Origin`                    | `Access-Control-Allow-Origin: https://example.com`                                                       | Controls which origins can access resources.                                                                    |
| `Access-Control-Allow-Methods`                   | `Access-Control-Allow-Methods: GET, POST`                                                                | Defines allowed HTTP methods for CORS requests.                                                                 |
| `Access-Control-Allow-Headers`                   | `Access-Control-Allow-Headers: Content-Type, Authorization`                                              | Defines allowed custom headers in cross-origin requests.                                                        |
| `Access-Control-Allow-Credentials`               | `Access-Control-Allow-Credentials: true`                                                                 | Allows cross-origin requests to include credentials (cookies, headers).                                         |
| **Referrer / Privacy**                           |                                                                                                          |                                                                                                                 |
| `Referrer-Policy`                                | `Referrer-Policy: no-referrer-when-downgrade`                                                            | Controls how much referrer info is sent in requests (protects privacy).                                         |
| `Permissions-Policy` (formerly `Feature-Policy`) | `Permissions-Policy: geolocation=(), microphone=()`                                                      | Restricts browser features/APIs (like camera, mic, geolocation).                                                |
| `Cross-Origin-Embedder-Policy` (COEP)            | `Cross-Origin-Embedder-Policy: require-corp`                                                             | Prevents embedding cross-origin resources unless explicitly allowed.                                            |
| `Cross-Origin-Opener-Policy` (COOP)              | `Cross-Origin-Opener-Policy: same-origin`                                                                | Isolates browsing context from other origins (mitigates XS-Leaks).                                              |
| `Cross-Origin-Resource-Policy` (CORP)            | `Cross-Origin-Resource-Policy: same-site`                                                                | Restricts which origins can load the resource.                                                                  |
| **Miscellaneous Security Headers**               |                                                                                                          |                                                                                                                 |
| `Expect-CT` _(deprecated)_                       | `Expect-CT: enforce, max-age=30`                                                                         | Used to enforce Certificate Transparency logs.                                                                  |
| `Report-To`                                      | `Report-To: {"group":"csp-endpoint","max_age":10886400,"endpoints":[{"url":"https://example.com/csp"}]}` | Defines endpoint for browser to send security reports.                                                          |
| `NEL` (Network Error Logging)                    | `NEL: {"report_to":"default","max_age":86400,"include_subdomains":true}`                                 | Lets browsers report network errors to a given endpoint.                                                        |
