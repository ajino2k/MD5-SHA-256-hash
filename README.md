# MD5-SHA-256-hash-command-line-in-Linux

### Generate a MD5

```echo -n password | md5sum | awk '{print $1}'``` </br>
```5f4dcc3b5aa765d61d8327deb882cf99```

### Convert to uppercase

```echo -n password | md5sum | awk '{print toupper($1)}'``` </br>
```5F4DCC3B5AA765D61D8327DEB882CF99```

### Generate a SHA-256

```echo -n password | sha256sum | awk '{print $1}'```
```5e884898da28047151d0e56f8dc6292773603d0d6aabbdd62a11ef721d1542d8```

### Convert to uppercase

```echo -n password | sha256sum | awk '{print toupper($1)}'```
```5E884898DA28047151D0E56F8DC6292773603D0D6AABBDD62A11EF721D1542D8```


### Verifying that a Private Key Matches a Certificate

```openssl x509 -noout -text -in server.crt```  
```openssl rsa -noout -text -in server.key```  

The `modulus' and the `public exponent' portions in the key and the Certificate must match. But since the public exponent is usually 65537 and it's bothering comparing long modulus you can use the following approach:

```openssl x509 -noout -modulus -in server.crt | openssl md5```  
```openssl rsa -noout -modulus -in server.key | openssl md5```  

And then compare these really shorter numbers. With overwhelming probability they will differ if the keys are different. As a one-liner:

```openssl x509 -noout -modulus -in server.pem | openssl md5 ;\```  
```openssl rsa -noout -modulus -in server.key | openssl md5```  

And with auto-magic comparison (If more than one hash is displayed, they don't match):

```(openssl x509 -noout -modulus -in server.pem | openssl md5 ;\```  
```openssl rsa -noout -modulus -in server.key | openssl md5) | uniq```  
   
BTW, if I want to check to which key or certificate a particular CSR belongs you can compute

```openssl req -noout -modulus -in server.csr | openssl md5```  
