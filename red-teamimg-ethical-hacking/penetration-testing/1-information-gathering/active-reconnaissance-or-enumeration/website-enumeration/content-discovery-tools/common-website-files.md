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

## **Sitemap.xml**

Unlike the robots.txt file, which restricts what search engine crawlers can look at, the sitemap.xml file gives a list of every file the website owner wishes to be listed on a search engine. These can sometimes contain areas of the website that are a bit more difficult to navigate to or even list some old webpages that the current site no longer uses but are still working behind the scenes.

```xml
<urlset>
<url>
<loc>http://10.10.145.106/</loc>
<lastmod>2021-07-19T13:07:32+00:00</lastmod>
<priority>1.00</priority>
</url>
<url>
<loc>http://10.10.145.106/news</loc>
<lastmod>2021-07-19T13:07:32+00:00</lastmod>
<priority>0.80</priority>
</url>
<url>
<loc>http://10.10.145.106/news/article?id=1</loc>
<lastmod>2021-07-19T13:07:32+00:00</lastmod>
<priority>0.80</priority>
</url>
<url>
<loc>http://10.10.145.106/news/article?id=2</loc>
<lastmod>2021-07-19T13:07:32+00:00</lastmod>
<priority>0.80</priority>
</url>
<url>
<loc>http://10.10.145.106/news/article?id=3</loc>
<lastmod>2021-07-19T13:07:32+00:00</lastmod>
<priority>0.80</priority>
</url>
<url>
<loc>http://10.10.145.106/contact</loc>
<lastmod>2021-07-19T13:07:32+00:00</lastmod>
<priority>0.80</priority>
</url>
<url>
<loc>http://10.10.145.106/customers/login</loc>
<lastmod>2021-07-19T13:07:32+00:00</lastmod>
<priority>0.80</priority>
</url>
<url>
<loc>http://10.10.145.106/s3cr3t-area</loc>
<lastmod>2021-07-19T13:07:32+00:00</lastmod>
<priority>0.80</priority>
</url>
</urlset>
```
