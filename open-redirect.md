# Open Redirect

```
URL 
    Absolute: https://google.com 
    Relative 
        ?url=/login 

Exploit + Automation 

    1) Burp , 301 302 -> Intruder 
    2) wayback + oralyzer

```

```
waybackurls testphp.vulnweb.com | gf redirect  | qsreplace  -a | while read domain; do python3 oralyzer.py -u $domain; done            
```

```
Open Redirect -> XSS -> javascript:alert(1) 
```
