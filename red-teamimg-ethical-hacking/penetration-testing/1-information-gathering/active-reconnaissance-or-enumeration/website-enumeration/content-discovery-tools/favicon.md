# Favicon

```markup
PS C:\> curl https://static-labs.tryhackme.cloud/sites/favicon/images/favicon.ico -UseBasicParsing -o favicon.ico

PS C:\> Get-FileHash .\favicon.ico -Algorithm MD5 
```

Sometimes when frameworks are used to build a website, a favicon that is part of the installation gets leftover, and if the website developer doesn't replace this with a custom one, this can give us a clue on what framework is in use. OWASP host a database of common framework icons that you can use to check against the targets favicon [https://wiki.owasp.org/index.php/OWASP\_favicon\_database](https://wiki.owasp.org/index.php/OWASP_favicon_database). Once we know the framework stack, we can use external resources to discover more about it (see next section).

<br>
