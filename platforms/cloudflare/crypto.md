# Crypto

The crypto section is used for everything relating to SSL certificates, TLS and HTTPS rewriting.

Click on the Crypto tab to get started: 

![Crypto tab](images/crypto/crypto-tab.jpg "Crypto tab")

## SSL

The SSL panel shows the status of your CloudFlare certificate and allows you to control how strict SSL will be. There are 
multiple options for the strictness of the SSL connection.

* Off - SSL is completely disabled and traffic will be routed via HTTP.
* Flexible - Traffic can either use HTTP or HTTPS however requests to your origin server are sent via HTTP.
* Full - Traffic is sent using HTTPS but requests to your origin server are sent via HTTP.
* Full (strict) - Traffic is sent only using HTTPS, including to your origin server. This requires a valid certificate
on your origin server.

## Edge Certificates

When CloudFlare sets up your site you are assigned an SSL certificate already. This certificate is used by multiple domains,
which means that it is shared by multiple CloudFlare customers. This certificate is used to encrypt traffic from the request 
to the CloudFlare servers - it is not used for connections to your origin server.


You can order a dedicated SSL certificate (min. 5 USD per month) which is automatically renewed upon expiry.

## Origin Certificates

Origin Certificates are equivalent to a self-signed certificate and are not issued by a valid certification authority
(e.g. Verisign, Comodo). The origin certificate is used to install on your origin server so that you can make use of 
the `Full (strict)` option for your SSL settings. You can alternatively use Let's Encrypt on your origin server.

Generating an origin certificate is entirely free and can be valid for up to 15 years.

## HTTP Strict Transport Security (HSTS)

HSTS, HTTP Strict Transport Security, is a header which allows a website to specify and enforce a security policy in web browsers.
It prevents the site from being accessed from HTTP entirely and requires you to always have a valid SSL certificate set up. It is
important to note that once you have enabled HSTS, modifying the crypto settings to disabled SSL will make your site inaccessible.

You can read more about HSTS [here](https://blog.cloudflare.com/enforce-web-policy-with-hypertext-strict-transport-security-hsts).

You can submit your domain to the Chrome preload list [here](https://hstspreload.org).

## Authenticated Origin Pulls

Authenticated Origin Pulls allow you to cryptographically verify that requests to your origin server have come from CloudFlare using a TLS 
client certificate. This prevents clients from sending requests directly to your origin, bypassing security measures provided by CloudFlare, 
such as IP and Web Application Firewalls, logging, and encryption.

## Opportunistic Encryption

Opportunistic Encryption, when enabled, informs a clients browser that your site is available over HTTPS. It does not enforce HTTPS.

## Automatic HTTPS Rewrites

Automatic HTTPS Rewrites rewrites the URLs on your website to `https://` to prevent mixed content warnings and save you time from manually
updating URLs to `https://`. This will affect all resources on your site.