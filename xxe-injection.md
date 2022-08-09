# XXE Injection

```
- XML vs HTML 
- XXE Injection 
    - Read Local Files
    - SSRF 
    - RCE 
- https://portswigger.net/web-security/xxe/lab-exploiting-xxe-to-retrieve-files
- https://portswigger.net/web-security/xxe/lab-exploiting-xxe-to-perform-ssrf
- https://github.com/swisskyrepo/PayloadsAllTheThings/tree/master/Server%20Side%20Request%20Forgery
- https://portswigger.net/web-security/xxe/blind/lab-xxe-with-out-of-band-interaction
```

### entities

```
- general
- predefine
- parameter (%)
- external (SYSTEM)
- xinclude
```

### where to find

we shloud find content-type : application/xml.&#x20;

some times we use soap and we never see above header

### Parameter Entity

```
- https://portswigger.net/web-security/xxe/blind/lab-xxe-with-out-of-band-interaction-using-parameter-entities
```

### XInclude

```
- Hidden & Public Attack Surfaces
- https://www.xml.com/pub/a/2002/07/31/xinclude.html
- https://portswigger.net/web-security/xxe/lab-xinclude-attack
- <test xmlns:xi="http://www.w3.org/2001/XInclude"><xi:include parse="text" href="file:///etc/passwd"/></test>
```

### External DTD

```
- https://stackoverflow.com/questions/39549360/parameter-entities-in-internal-dtd
- https://portswigger.net/web-security/xxe/blind/lab-xxe-with-out-of-band-exfiltration
- OOB Detection -> Data Exfiltration
```

### automation

```
- Autorepeater + XXEXploiter 
    - https://github.com/luisfontes19/xxexploiter
```

### Bilion Laugh Attack

```
- PCDATA – parsed character data. It parses all the data in an XML document.
- CDATA – unparsed character Data. This is the data that should not be parsed further in an xml document.
```

