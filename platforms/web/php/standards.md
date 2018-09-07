# PHP Standards and Style Guide
*   [Introduction](#introduction)
    *   [PHP](#php)
        *   [PSR-1](#php)   
        *   [PSR-2](#php)   
    *   [Laravel](#laravel)
    *   [RESTful API's](#restful)
*   [Amendments](#amendments)
    *   [Variables](#variables)
    *   [Methods](#methods)
*   [Adhering to standards](#adhering)
    *   [PhpStorm + PHP Code Sniffer](#codesniffer)
    *   [PhpStorm + PHP-CS-Fixer](#csfixer)



<h3 id="introduction">Introduction</h3>
Our goal isn’t to rewrite the unspoken rules of languages - and most of what we’re looking for is defined in the relevant documentation. 

The below documentation links should be followed unless defined otherwise in this document.

<h4 id="php">PHP</h4>

   * [PSR-1](https://www.php-fig.org/psr/psr-1/)
   * [PSR-2](https://www.php-fig.org/psr/psr-2/)
   
<h4 id="laravel">Laravel</h4>

   * [Laravel Documentation](https://laravel.com/docs/)

<h4 id="restful">RESTful API's</h4>

   * [Best Practices for a pragmatic RESTful API](https://www.vinaysahni.com/best-practices-for-a-pragmatic-restful-api)

With how we work being heavily framework based - these frameworks (especially Laravel) offer a TON of stuff to stop us from making messy code. A lot of the time this stuff will not be obvious unless you’re looking for it, so looking through the documentation top to bottom should be homework for everyone’s first encounter with the framework (If you haven’t done this, please do).

<h3 id="amendments">Amendments</h3>
Below are a list of exceptions that do not fall within the above documents. Sections marked in gray are proposed amendments, and are pending discussion to approval/rejection.

Discussions will be had every other Friday at close of play to discuss/vote on whether the proposed amendment gets approved. In favour of keeping the standards as simple as possible - an amendment must have an approval rate of over 60%.

<h4 id="variables">Variables</h4>
Variable names MUST be defined in camelCase

<h4 id="methods">Methods</h4>
Opening braces for methods MUST be on the same line as the declaration, and closing braces MUST go on the next line after the body.

<h3 id="adhering">Adhering to standards</h3>
It’s all well and good having a set standard outlined - but following it can be difficult unless you’re always thinking about following it.

There are a few methods of adhering to these standards which we will be implementing.

<h4 id="codesniffer">PhpStorm + PHP Code Sniffer</h4>
PhpStorm has support for PHP Sniffer, which enables live, in-IDE prompts to fix stylings. We can develop a custom setup to handle these extra rules, or at the least default it to PSR-2.

You can see Jetbrains’ guide to configuration [here](https://confluence.jetbrains.com/display/PhpStorm/PHP+Code+Sniffer+in+PhpStorm)

<h4 id="csfixer">PhpStorm + PHP-CS-Fixer</h4>
A similar solution to the above is PHP CS Fixer. It’s not as easy to integrate live into your IDE but there are a number of guides to do so. The benefit of this one is that it’s the same engine that Style CI uses, which in turn ensures that there aren’t any unexpected PR blocks from the CI service.
