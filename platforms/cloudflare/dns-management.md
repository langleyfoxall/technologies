# DNS Management

The DNS section provides a fast and really easy interface to update your DNS records. 

Click on the DNS tab to get started: 

![DNS tab](images/dns-management/dns-tab.jpg "DNS tab")

## DNS Records

This panel shows your domains DNS records. You may update these as much as you would like, the changes should be reflected 
almost immediately. If you are adding A, AAAA, or CNAME records you can optionally route these through the CloudFlare network
for enhanced performance and security by making sure the cloud is orange. You may disable and enable the routing freely
since this will not directly cause an error on your website or cause downtime - disabling this option will expose your origin 
servers IP address.


* Orange cloud - CloudFlare is routing the traffic through its network.
* Grey cloud - CloudFlare is only active as a DNS and is not routing the traffic through its network.

You can add extra records by completing the input form in the header of the panel. It should look similar to the picture below.
You will be informed of any issues with your inputted information prior to the record getting deployed.

![Add DNS record](images/dns-management/add-dns-record.jpg "Add DNS record")

### Adding an AWS S3 bucket

You can optionally route your S3 bucket through CloudFlare to reduce the cost of your S3 bandwidth usage. This is useful if you are
running a large site and are experiencing high bandwidth costs on S3. It reduces cost by caching the image on CloudFlare's servers and
using that image when processing requests instead of always requesting the same file from your S3 bucket.

1. Create a new CNAME record using your S3 bucket name. Please ensure you do not use anything other than your S3 bucket name since this
is a AWS requirement.
![DNS tab](images/dns-management/add-s3-bucket.png "DNS tab")

2. You can now update your frameworks configuration to use the new DNS record we created. For this example we will use Laravel and
update the `.env` file to include the following.

`AWS_URL=files.example.com.s3.amazonaws.com`

## Cloudflare Nameservers

This panel shows your nameservers that need to be assigned to your domain in order for you to use CloudFlare. This will have been
explained to you during the domain setup process.