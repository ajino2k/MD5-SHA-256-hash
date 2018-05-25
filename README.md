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
