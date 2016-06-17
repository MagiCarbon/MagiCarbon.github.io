---
layout: post
categories: blog
share: true
comments: true
title: openssl create SCR with multiple SANs
excerpt: openssl stuff
date: '2016-04-14T15:50:00+08:00'
#modified: '2014-11-09T23:39:00+01:00'
tags: [openssl, https]
author: MC
hidelogo: true
---

## GOAL

one certificate works with multiple subdomain.

### first config openssl-san.cnf

mkdir test-san && cd test-san
cp /etc/ssl/openssl.cnf ./openssl-san.cnf

add the followings:

```
[req]
req_extensions = v3_req

[ v3_req ]

# Extensions to add to a certificate request

basicConstraints = CA:FALSE
keyUsage = nonRepudiation, digitalSignature, keyEncipherment
subjectAltName = @alt_names

[alt_names]
DNS.1 = test.com
DNS.2 = www.test.com
DNS.3 = mail.test.com
```

### then create new key with password

openssl genrsa -passout stdin -out server.key 2048

*or*

ssh-askpass | openssl genrsa -passout stdin -out server.key 2048

### finally create the CSR file

openssl req -new -out req.csr -key server.key -config openssl-san.cnf

*__check SANs__*

*openssl req -text -noout -in req.csr*


[CAcert wiki](http://wiki.cacert.org/FAQ/subjectAltName){:target="_blank"}
