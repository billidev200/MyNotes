# ESI Injection

**ESI (Edge Side Includes)** is a markup language that allows CDNs or reverse proxies to assemble pages dynamically at the _edge_, instead of the origin server.

```
<esi:include src="/user/profile" />
```

When a CDN/proxy sees this, it fetches `/user/profile` and inserts it into the response before sending it to the client.
