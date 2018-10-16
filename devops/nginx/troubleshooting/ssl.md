## SSL

### Enabling support for older devices & browsers

You can enable supprot for older devices & browsers by updating `ssl_protocols` and `ssl_ciphers`. `ssl_protocols` define the TLS versions the web server should allow and `ssl_ciphers` defines the supported ciphers. 

When you first setup a site through Laravel Forge and enable the Let's Encrypt certificate the default protocols and ciphers are the following.

```
    ssl_protocols TLSv1.2;
    ssl_ciphers ECDHE-RSA-AES256-GCM-SHA512:DHE-RSA-AES256-GCM-SHA512:ECDHE-RSA-AES256-GCM-SHA384:DHE-RSA-AES256-GCM-SHA384:ECDHE-RSA-AES256-SHA384;
```

Using this configuration limits connections to TLS v1.2 and newer devices and browsers. It is generally not recommended to support less than TLS v1.1 due to downgrade attacks and other vulnerabilities in TLS v1.0 and below.

If you wish to support older devices (but weaken security in the process) then the following configuration is recommended.

```
ssl_protocols TLSv1.1 TLSv1.2;
ssl_ciphers "EECDH+AESGCM:EDH+AESGCM:AES256+EECDH:AES256+EDH:ECDHE-RSA-AES128-GCM-SHA384:ECDHE-RSA-AES128-GCM-SHA256:ECDHE-RSA-AES128-GCM-SHA128:DHE-RSA-AES128-GCM-SHA384:DHE-RSA-AES128-GCM-SHA256:DHE-RSA-AES128-GCM-SHA128:ECDHE-RSA-AES128-SHA384:ECDHE-RSA-AES128-SHA128:ECDHE-RSA-AES128-SHA:ECDHE-RSA-AES128-SHA:DHE-RSA-AES128-SHA128:DHE-RSA-AES128-SHA128:DHE-RSA-AES128-SHA:DHE-RSA-AES128-SHA:ECDHE-RSA-DES-CBC3-SHA:EDH-RSA-DES-CBC3-SHA:AES128-GCM-SHA384:AES128-GCM-SHA128:AES128-SHA128:AES128-SHA128:AES128-SHA:AES128-SHA:DES-CBC3-SHA:HIGH:!aNULL:!eNULL:!EXPORT:!DES:!MD5:!PSK:!RC4";
```

You can optionally change the `ssl_protocols` to use TLS v1.0 instead, however this is not recommended.

```
ssl_protocols TLSv1 TLSv1.1 TLSv1.2; 
```

A good place to look for configurations for older devices and recommended configurations (for many different web servers) is [Cipherli.st](https://cipherli.st).