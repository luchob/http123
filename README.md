# Introduction

This repo contains couple of files and configurations which enable the comparison of HTTP1/2 protocols. HTTP/3 is not yet configured. The base server is nginx. As SSL certificate is needed a self-signed one is included.


## Generation of a Self Signed Certificate

The repository comes with a self-signed certificate. If you want yours, follow the steps below. 

_STEP 1:_ Create the server private key

```
openssl genrsa -out cert.key 2048
```

_STEP 2:_ Create the certificate signing request (CSR)

```
openssl req -new -key cert.key -out cert.csr
```

_STEP 3:_ Sign the certificate using the private key and CSR

```
openssl x509 -req -days 3650 -in cert.csr -signkey cert.key -out cert.crt
```

## Starting with HTTP/2

Use the docker compose provided as is. Use [https://localhost](https://localhost).

## Starting with HTTP/1

In [nginx.conf](config/nginx.conf) change `http2 on` to `http2 off` 
