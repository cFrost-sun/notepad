### 生成证书
```
sudo ./letsencrypt-auto certonly --standalone --email admin@eulerproject.io -d eulerproject.io -d www.eulerproject.io -d ci.eulerproject.io -d repo.eulerproject.io -d www.uat.eulerproject.io
```

### 证书续期

```
sudo ./letsencrypt-auto certonly --renew --email admin@eulerproject.io -d eulerproject.io -d www.eulerproject.io -d ci.eulerproject.io -d repo.eulerproject.io -d www.uat.eulerproject.io
```

### 生成dhparam
```
openssl dhparam -out dhparam.pem 2048
```

### Nginx配置
```
server {
    listen      443;
    server_name eulerproject.io www.eulerproject.io;

    ssl on;
    ssl_certificate /etc/letsencrypt/live/eulerproject.io/fullchain.pem;
    ssl_certificate_key /etc/letsencrypt/live/eulerproject.io/privkey.pem;
    ssl_trusted_certificate /etc/letsencrypt/live/eulerproject.io/chain.pem;
    ssl_ciphers 'ECDHE-RSA-AES128-GCM-SHA256:ECDHE-ECDSA-AES128-GCM-SHA256:ECDHE-RSA-AES256-GCM-SHA384:ECDHE-ECDSA-AES256-GCM-SHA384:DHE-RSA-AES128-GCM-SHA256:DHE-DSS-AES128-GCM-SHA256:kEDH+AESGCM:ECDHE-RSA-AES128-SHA256:ECDHE-ECDSA-AES128-SHA256:ECDHE-RSA-AES128-SHA:ECDHE-ECDSA-AES128-SHA:ECDHE-RSA-AES256-SHA384:ECDHE-ECDSA-AES256-SHA384:ECDHE-RSA-AES256-SHA:ECDHE-ECDSA-AES256-SHA:DHE-RSA-AES128-SHA256:DHE-RSA-AES128-SHA:DHE-DSS-AES128-SHA256:DHE-RSA-AES256-SHA256:DHE-DSS-AES256-SHA:DHE-RSA-AES256-SHA:AES128-GCM-SHA256:AES256-GCM-SHA384:AES128-SHA256:AES256-SHA256:AES128-SHA:AES256-SHA:AES:CAMELLIA:DES-CBC3-SHA:!aNULL:!eNULL:!EXPORT:!DES:!RC4:!MD5:!PSK:!aECDH:!EDH-DSS-DES-CBC3-SHA:!EDH-RSA-DES-CBC3-SHA:!KRB5-DES-CBC3-SHA';
    ssl_prefer_server_ciphers on;
    ssl_dhparam pathto/dhparam.pem;

    ...

}
```
