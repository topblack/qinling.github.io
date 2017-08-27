---
layout: post
title: NodeJS Unexpected token ...
date: 2017-08-26 16:54:00 +0800
---
# NodeJS: Unexpected token ...
```
SyntaxError: Unexpected token ...
    at exports.runInThisContext (vm.js:53:16)
    at Module._compile (module.js:374:25)
    at Object.Module._extensions..js (module.js:417:10)
    at Module.load (module.js:344:32)
    at Function.Module._load (module.js:301:12)
    at Module.require (module.js:354:17)
    at require (internal/module.js:12:17)
    at Object.<anonymous> (/jenkins-assistant/node_modules/nodemailer/lib/nodemailer.js:3:16)
    at Module._compile (module.js:410:26)
    at Object.Module._extensions..js (module.js:417:10)
/jenkins-assistant/node_modules/nodemailer/lib/mailer/index.js:31
            compile: [(...args) => this._convertDataImages(...args)],
                       ^^^

SyntaxError: Unexpected token ...
    at exports.runInThisContext (vm.js:53:16)
    at Module._compile (module.js:374:25)
    at Object.Module._extensions..js (module.js:417:10)
    at Module.load (module.js:344:32)
    at Function.Module._load (module.js:301:12)
    at Module.require (module.js:354:17)
    at require (internal/module.js:12:17)
    at Object.<anonymous> (/jenkins-assistant/node_modules/nodemailer/lib/nodemailer.js:3:16)
    at Module._compile (module.js:410:26)
    at Object.Module._extensions..js (module.js:417:10)
```

https://github.com/sahat/hackathon-starter/issues/688

https://askubuntu.com/questions/426750/how-can-i-update-my-nodejs-to-the-latest-version

