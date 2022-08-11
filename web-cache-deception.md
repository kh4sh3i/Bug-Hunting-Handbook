# Web Cache Deception

if /profile exist and /profile/test.js show /profile page that contains sensitive data, then cache engine store test.js file and we can access to this data without login !

```
- https://www.blackhat.com/docs/us-17/wednesday/us-17-Gil-Web-Cache-Deception-Attack.pdf 
- https://github.com/carlospolop/hacktricks/blob/master/pentesting-web/cache-deception.md
- https://blog.mindedsecurity.com/2021/01/demystifying-web-cache-threats.html
- https://omergil.blogspot.com/2017/02/web-cache-deception-attack.html
    - web cache deception + CSRF
        - https://ravinacademy.com/%D8%A2%D8%B3%DB%8C%D8%A8%E2%80%8C%D9%BE%D8%B0%DB%8C%D8%B1%DB%8C-account-takeover-%D8%AF%D8%B1-%D8%A8%D8%B1%D9%86%D8%A7%D9%85%D9%87%E2%80%8C%DB%8C-%D8%A8%D8%A7%D9%86%D8%AA%DB%8C-ebay/
```

### automation

{% embed url="https://portswigger.net/bappstore/7c1ca94a61474d9e897d307c858d52f0" %}
