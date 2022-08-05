# postMessage

* Window Objects: The window object represents an open window in a browser
  * W1 -> W2

### postMessage Components

DOM XSS

Info Disclosure

* postMessage Components
  * sender -> listener

### Case-1: DOM XSS

if listener use sink with dynamic value, and use "\*" origin we can use this vuln

```
- Case-1: DOM XSS
    - Detection: Debugging: 'message' event handlers -> Firefox: ctrl + shift + f: 'message'   
    - Exploitation:
        - Using Iframe
        - Using window.open
```

### Case-2: Info Disclosure

if sender send sensitive data like token,crsf,password,.. and use "\*" in origin we can use this vuln

```
    - *.postMessage(data, '*')
    - Exploitation:
        - set message listener 
```

### Detection

```
    - https://github.com/fransr/postMessage-tracker
    - DOM Invader
    - https://github.com/projectdiscovery/nuclei-templates/blob/master/headless/postmessage-outgoing-tracker.yaml
    - nuclei -l urls -t nuclei-templates/headless/postmessage-outgoing-tracker.yaml --headless 
```

### chaining

```
 - postMessage -> dom xss + info disclosure
 - csrf 
  - token -> value + filed -> 5 bug ?
  - authenticated path -> .postmessage(token, '*')
  - listener -> token -> form -> request (update) -> csrf
```

