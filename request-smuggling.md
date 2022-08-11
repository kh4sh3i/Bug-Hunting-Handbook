# Request Smuggling

```
- HTTP: https://datatracker.ietf.org/doc/html/rfc7230#section-3.3.3 
    - Content-Length 
    - Transfer-Encoding 
    - TE-CL Example
        POST /endpoint HTTP/1.1
        Host: target.com 
        Transfer-Encoding: chunked 
        Content-Length: 9

        4\r\n size_ [CRLF] 
        data\r\n
        0
```

### chains

```
 1- Capturing other reuquests
 - https://portswigger.net/web-security/request-smuggling/lab-basic-cl-te
    - differential responses 
    - timing techniques 
2- self-xss + Request Smuggling
    - https://portswigger.net/web-security/request-smuggling/exploiting/lab-deliver-reflected-xss
3- Web Cache Deception + Request Smuggling 
    - https://portswigger.net/web-security/request-smuggling/exploiting/lab-perform-web-cache-deception
4- Web Cache Poisoning/On-Site Redirection + Request Smuggling  
    - https://portswigger.net/web-security/request-smuggling/exploiting/lab-perform-web-cache-poisoning
```
