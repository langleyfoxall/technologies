# CloudFlare 

## What is CloudFlare?

CloudFlare is a Content Delivery Network, DNS management tool, HTTP proxy and provides DDoS mitigation. The idea behind CloudFlare 
is to provide a faster and more secure web free of charge.

## What is a Content Delivery Network?

A content delivery network does what it says in the name, it delivers content. The difference between delivering content from your 
origin server and delivering it through a CDN can be quite significant for performance. CDN's deliver content from the closest data center
to the initial request that the user makes. After one request is made to your origin server to fetch the files (e.g. images), CloudFlare 
then caches the files, optimises the files and stores it on their data center network so that the files decrease in load times and 
in some cases file size.

You can see the list of CloudFlare data centers [here](https://www.cloudflare.com/network).

## What is a HTTP proxy?

A HTTP proxy sits between your origin server and the users request to forward the request to your origin server. This can mask your 
origin servers IP address to prevent attackers from directly attacking your origin server. 

CloudFlare sits between your origin server and the users request to provide additional security features (e.g. Web Application Firewall),
block particular IP addresses or regions, and to improve general request performance (response times). 

## Documentation

* [DNS Management](dns-management.md) - Overview of the DNS page and how to add records.
* [Crypto](crypto.md) - Overview of the Crypto page and how it affects SSL.
* [Speed](speed.md) - Overview of the Speed page and general performance improvements.
* [Caching](caching.md) - Overview of the Caching page and the purging of assets.

## Notes

* CloudFlare has a limit of 100MB for an upload, per request, on the Free plan.
* Enabling the Rocket Loader can potentially break the JavaScript functionality across the site or on certain pages.

## Useful Links

* [CloudFlare](https://www.cloudflare.com)
* [Brief Overview](https://youtu.be/T47T_mG7YbU)
* [API Documentation (v4)](https://api.cloudflare.com)
* [PHP SDK](https://github.com/cloudflare/cloudflare-php)
* [Resources](https://www.cloudflare.com/resources)
* [Service Status](https://www.cloudflarestatus.com/)
