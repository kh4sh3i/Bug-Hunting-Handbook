# CORS

### XHR & XHR Components

```
https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest  
https://www.w3schools.com/xml/tryit.asp?filename=tryxml_httprequest
Response Type
    responseText
    responseXML
```

### SOP & CORS

```
A -> B (Same Origin Policy) 
same protocol, same host, same port
https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS 
https://portswigger.net/web-security/cors/lab-basic-origin-reflection-attack
```

### null origin usage

```
    Requests from serialized data
    Request using the file: protocol (local HTML files)
    Sandboxed cross-origin requests
https://portswigger.net/web-security/cors/lab-null-origin-whitelisted-attackC
```

### Cors + xss&#x20;

if we find acces-control-allow-origin = test.target.com , then we find xss in test subdomain, we can call cors from this subdomain and booom!

```
https://portswigger.net/web-security/cors/lab-breaking-https-attack
```

### Tips

if access-control-allow-origin = \* , then we can not attack !&#x20;

because in RFC if above header is set to wildcard (\*) then we can not use access-controll-allow-credential = true !

when we find cors vuln, we should create xhr request and insert in valid site and send link to victim, after loged in user see this site, data send to attacker

### Automation

```
echo https://google.com | hakrawler -u | httpx | CorsMe 
```
