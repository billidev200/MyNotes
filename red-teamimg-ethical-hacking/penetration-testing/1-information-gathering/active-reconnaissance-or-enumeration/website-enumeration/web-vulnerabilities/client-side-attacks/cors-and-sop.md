# CORS & SOP



{% embed url="https://www.youtube.com/watch?v=4KHiSt0oLJ0" %}

## Understanding SOP

Same-origin policy or SOP is a policy that instructs how web browsers interact between web pages. According to this policy, a script on one web page can access data on another only if both pages share the same origin. This "origin" is identified by combining the URI scheme, hostname, and port number. The image below shows what a URL looks like with all its features (it does not use all features in every request).

<figure><img src="../../../../../../../.gitbook/assets/f750c8230ca04378b11f320d4b720640.png" alt=""><figcaption></figcaption></figure>

## Understanding CORS

Cross-Origin Resource Sharing (CORS) is a mechanism defined by HTTP headers that allows servers to specify how resources can be requested from different origins. While the Same-Origin Policy (SOP) restricts web pages by default to making requests to the same domain, CORS enables servers to declare exceptions to this policy, allowing web pages to request resources from other domains under controlled conditions.

**Different HTTP Headers Involved in CORS**

1. **Access-Control-Allow-Origin**: This header specifies which domains are allowed to access the resources. For example, `Access-Control-Allow-Origin: example.com` allows only requests from `example.com`.
2. **Access-Control-Allow-Methods**: Specifies the HTTP methods (GET, POST, etc.) that can be used during the request.
3. **Access-Control-Allow-Headers**: Indicates which HTTP headers can be used during the actual request.
4. **Access-Control-Max-Age**: Defines how long the results of a preflight request can be cached.
5. **Access-Control-Allow-Credentials**: This header instructs the browser whether to expose the response to the frontend JavaScript code when credentials like cookies, HTTP authentication, or client-side SSL certificates are sent with the request. If Access-Control-Allow-Credentials is set to true, it allows the browser to access the response from the server when credentials are included in the request. It's important to note that when this header is used, Access-Control-Allow-Origin cannot be set to \* and must specify an explicit domain to maintain security.

**Common Scenarios Where CORS is Applied**

CORS is commonly applied in scenarios such as:

1. **APIs and Web Services**: When a web application from one domain needs to access an API hosted on a different domain, CORS enables this interaction. For instance, a frontend application at `example-client.com` might need to fetch data from `example-api.com`.
2. **Content Delivery Networks (CDNs)**: Many websites use CDNs to load libraries like jQuery or fonts. CORS enables these resources to be securely shared across different domains.
3. **Web Fonts**: For web fonts to be used across different domains, CORS headers must be set, allowing websites to load fonts from a centralized location.
4. **Third-Party Plugins/Widgets:** Enabling features like social media buttons or chatbots from external sources on a website.
5. **Multi-Domain User Authentication:** Services that offer single sign-on (SSO) or use tokens (like OAuth) to authenticate users across multiple domains rely on CORS to exchange authentication data securely.

<figure><img src="../../../../../../../.gitbook/assets/Screenshot 2025-12-02 204007.png" alt=""><figcaption></figcaption></figure>

1. The browser first sends an HTTP request to the server.
2. The server then checks the Origin header against its list of allowed origins.
3. If the origin is allowed, the server responds with the appropriate `Access-Control-Allow-Origin` header.
4. The browser will block the cross-origin request if the origin is not allowed.
