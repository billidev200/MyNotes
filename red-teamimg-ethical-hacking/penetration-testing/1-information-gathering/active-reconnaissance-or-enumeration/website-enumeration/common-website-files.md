# Common Website files

## Robots.txt

Why is robots.txt important?\
\
&#x20;   Controls what parts of your website search engines can see.\
\
&#x20;   Helps prevent indexing of private, duplicate, or irrelevant pages.\
\
&#x20;   Saves server resources by limiting crawler traffic.\
\
&#x20;   Guides SEO by controlling crawl priorities.

```
https://example.com/robots.txt
```

```
User-agent: *
Disallow: /admin/
Disallow: /private/
Allow: /public/

User-agent: [name of the crawler or * for all]
Disallow: [URL path you want to block]
Allow: [URL path you want to allow]
```

| Term       | Explanation                                                   |
| ---------- | ------------------------------------------------------------- |
| robots.txt | Text file that tells crawlers what to crawl or not            |
| User-agent | Specifies which crawler the rule applies to (e.g., Googlebot) |
| Disallow   | Blocks crawlers from specified paths                          |
| Allow      | Allows crawlers access to specified paths                     |

## Sitemapxml

#### 🔧 How to Use

1. Save the file as `sitemap.xml`
2. Upload it to the root of your website:\
   `https://yourdomain.com/sitemap.xml`
3. Submit it in **Google Search Console** and **Bing Webmaster Tools**
