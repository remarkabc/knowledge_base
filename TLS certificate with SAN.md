# TLS certificate with SAN
* Generate CA
```
openssl req -x509 -sha256 -nodes -days 365 -newkey rsa:2048 -subj '/O=example Inc./CN=example.com' -keyout example_certs1/example.com.key -out example_certs1/example.com.crt
```

* Create our own custom ssl configuration file ```server_cert.cnf```

```
[req]
distinguished_name = req_distinguished_name
req_extensions = req_ext
prompt = no

[req_distinguished_name]
C   = CN
ST  = Shanghai
L   = Shanghai
O   = UFO
OU  = R&D
CN  = bitbucket.xin.test.com

[req_ext]
subjectAltName = @alt_names

[alt_names]
DNS.1 = xin.test.com
DNS.2 = *.xin.test.com
```

* Create CSR
```
openssl req -out server.csr -newkey rsa:2048 -nodes -keyout server.key -config server_cert.cnf
```
* Sign CSR
```
openssl x509 -req -days 365 -in server.csr -CA example_certs1/example.com.crt -CAkey example_certs1/example.com.key -CAcreateserial -out server.crt  -extensions req_ext -extfile server_cert.cnf
```
* Verify
```
openssl x509 -text -noout -in server.crt
```
