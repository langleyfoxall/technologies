# nginx

## What is nginx?

Nginx is open source software for web serving, reverse proxying, caching, load balancing, media streaming, and more. It started out as a web server designed for maximum performance and stability. In addition to its HTTP server capabilities, nginx can also function as a proxy server for email (IMAP, POP3, and SMTP) and a reverse proxy and load balancer for HTTP, TCP, and UDP servers.

## nginx vs Apache

We use nginx on all our servers due to its high performance, excellent security and Laravel Forge installs it by default. While Apache was and still is the most popular web server since it is the easiest web server to install and manage, it was not designed for high concurrency or todays internet traffic.

## Troubleshooting

* [SSL](troubleshooting/ssl.md) - SSL troubleshooting tips. Surrounding SSL, TLS, and backwards compatibility with older browsers/devices using ciphers.

## Useful commands

* `nginx -t` - Tests the configuration and outputs any issues with the modified configuration without reloading the web server. Running this after modifying the configuration makes sure your site isn't affected by any breaking changes and allows you to identify and resolve the issues quickly.