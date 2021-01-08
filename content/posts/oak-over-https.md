---
title: "Oak Over Https"
summary: "Integrando Oak com certificados SSL"
description: "Use HTTPS"
date: 2021-01-08T12:31:17-03:00
categories: Security
tags:
- https
- ssl
- tls
- backend
- server
- deno
- step-by-step
- oak
- openssl
- tool
- cli
- code
- frameworks
- programming
draft: false
---

## Dependencies

Primeiro devemos certificar que temos o programa `openssl`
```text
dpkg -l |grep openssl
```
deve aparescer algo como isto
```text
ii libgnutls-openssl27:amd64   2.12.23-12ubuntu2.4   amd64   GNU TLS library - OpenSSL wrapper

ii openssl   1.0.1f-1ubuntu2.16   amd64   Secure Sockets Layer toolkit - cryptographic utility
```

senão tiver o `openssl` instalado, instale com o comando:

_(debain based)_
```text
apt-get install openssl
```
## Generate Keys

Para gerar a chave privada e o certificado rode o comando:
```text
openssl req -x509 -newkey rsa:2048 -keyout keytmp.pem -out cert.pem -days 365
```

Depois gere a chave descriptografada:
```text
openssl rsa -in keytmp.pem -out key.pem
```

ja pode excluir o arquivo `keytmp.pem`, ele não será mais necessário.

## Use Oak with Key and Certificate

Para usar Oak com HTTPS devemos passar setar os atributos `secure`, `certFile` e `keyFile`.
como o exemplo a seguir:

```js
await App.listen(
  {
    port: 8000,
    secure: true,
    certFile: "./cert.pem",
    keyFile: "./key.pem",
  },
);
```
 
---
## referências

How To Create an HTTPS Server on Localhost using Express: [_https://medium.com/@nitinpatel_20236/how-to-create-an-https-server-on-localhost-using-express-366435d61f28_](https://medium.com/@nitinpatel_20236/how-to-create-an-https-server-on-localhost-using-express-366435d61f28)

oak docs: [_https://github.com/oakserver/oak_](https://github.com/oakserver/oak)

OpenSSL Tutorial: How Do SSL Certificates, Private Keys, & CSRs Work?: [_https://phoenixnap.com/kb/openssl-tutorial-ssl-certificates-private-keys-csrs_](https://phoenixnap.com/kb/openssl-tutorial-ssl-certificates-private-keys-csrs)
