# Deserialization

if we can access to source code we can find magic method and create class and set variable to make rce, lfi, xss ,... in code&#x20;

in advanced attack we use POP chain&#x20;

```
- PHP
    - Magic Methods
        - https://www.tutorialspoint.com/php-magic-methods
    - 1.php: __wakeup(), __sleep(): RCE Example
    - 2.php: __destruct()
    - 3: https://portswigger.net/web-security/deserialization/exploiting/lab-deserialization-modifying-serialized-objects
    - 4: POP Chain
```

```
- NodeJS
    - https://snyk.io/test/npm/node-serialize
    - Generate Serialize payload
    - self-invoking functions
```

```
- Java
    - https://portswigger.net/web-security/deserialization/exploiting/lab-deserialization-exploiting-java-deserialization-with-apache-commons
    - ysoserial: https://github.com/frohoff/ysoserial
    - java -jar path/to/ysoserial.jar CommonsCollections4 'rm /home/carlos/morale.txt' | base64
    - https://github.com/mandiant/heyserial/blob/main/utils/generate_payloads.sh
    - Burp Extension: Java Deserialization Scanner
```

```
- .Net
    - https://github.com/pwntester/ysoserial.net
```

### automation

```
- https://github.com/frohoff/ysoserial
- https://github.com/pwntester/ysoserial.net
```

