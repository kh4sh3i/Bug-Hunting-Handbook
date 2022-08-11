# Web Cache Poisoning

```
- Cache Keys 
    - Client -> Caching Server -> Server 
    - GET  /endpoint 
      Host: target.com 
      X-Default: black 

    - GET /endpoint 
      Host: target.com
      X-Default: red 
      
- Unkeyed Inputs 
    - GET /endpoint 
      Host: target.com 
      X-Forwarded-Host: value 
```

### Methodology

```
    - Unkeyed Inputs 
    - Fuzzing -> Param Miner 
    - Param Miner -> Inputs -> Response?
    https://portswigger.net/web-security/web-cache-poisoning/exploiting-implementation-flaws/lab-web-cache-poisoning-unkeyed-param
```

### automation

```
    - Domains (Recon) -> Nuclei 
    - Param Miner
    - Scanner: https://github.com/Hackmanit/Web-Cache-Vulnerability-Scanner
```
