# Speed

The Speed page on CloudFlare allows you manage asset minification and compression.

Go to the Speed tab to get started

![Speed tab](images/speed/speed-tab.jpg "Speed tab")

## Auto Minify

The auto minify options allow you minify your static assets to reduce the overall page size sent to your clients. 
This includes JavaScript, HTML and CSS. It will attempt to remove whitespace, comments and apply compression to your
static assets.

## Brotli

Brotli is an open source compression format created by Google. Instead of using the standard gzip compression that is enabled
by default on nginx, you can switch it out for Brotli - which is a more optimised compression format - to increase general website
performance. If the client does not support Brotli compression, CloudFlare will recognise this and use gzip for that request instead.

You can visit the GitHub repository [here](https://github.com/google/brotli).

## Rocket Loader

Rocket Loader attempts to asynchronously load JavaScript files, including third party libraries, to prevent blocking of the page load.
This can have a positive affect on Search Engine Optimisation however, it can potentially break some page functionality if it heavily
relies on JavaScript.

Usage of rocket loading heavily depends on your use-case since it can potentially break React as well as other third party libraries.

