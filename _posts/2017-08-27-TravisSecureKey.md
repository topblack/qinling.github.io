---
layout: post
title: Use secure keys in Travis ...
date: 2017-08-26 16:54:00 +0800
category: Travis
---

https://docs.travis-ci.com/user/encryption-keys/

# Brief
Travis provides a travis cli tool for developers to encrypt the sensitive data locally before submitting them to the repo.
The tool can encrypt a plain text or a file. During encryption, it saves encryption key and IV to travis. This is why before calling the encryption command, you have to execute travis login first. After got the encrypted text or file, the encrypted version can be submitted to the repo. And in the build script, perform decrypt first.

# Encrypting Files
## Prerequisites

Before following the examples in this guide, make sure you have already

installed the Travis CI Command Line Client by running 
```
$ gem install travis
```

logged in to Travis CI using
```
$ travis login
``` 
or 

```
$ travis login --pro
```

## Encrypt file
```
$ travis encrypt-file super_secret.txt
```

## Add step to the .travis.yml
```
openssl aes-256-cbc -K $encrypted_0a6446eb3ae3_key -iv $encrypted_0a6446eb3ae3_iv -in super_secret.txt.enc -out super_secret.txt -d
```

You can also use --add to have it automatically add the decrypt command to your .travis.yml
