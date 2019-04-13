# PHP Standards and Style Guide
*   [Introduction](#introduction)
    *   [PHP](#php)
        *   [PSR-1](#php)   
        *   [PSR-2](#php)   
*   [Amendments](#amendments)
    *   [Variables](#variables)
    *   [Methods](#methods)
*   [Adhering to standards](#adhering-to-standards)
    *   [PhpStorm + PHP Code Sniffer](#phpstorm--php-code-sniffer)
    *   [PhpStorm + PHP-CS-Fixer](#phpstorm--php-cs-fixer)

### Introduction
Our goal isn’t to rewrite the unspoken rules of languages - and most of what we’re looking for is defined in the relevant documentation. 

The below documentation links should be followed unless defined otherwise in this document.

#### PHP

   * [PSR-1](https://www.php-fig.org/psr/psr-1/)
   * [PSR-2](https://www.php-fig.org/psr/psr-2/)

With how we work being heavily framework based - these frameworks (especially Laravel) offer a TON of stuff to stop us from making messy code. A lot of the time this stuff will not be obvious unless you’re looking for it, so looking through the documentation top to bottom should be homework for everyone’s first encounter with the framework (If you haven’t done this, please do).

### Amendments
Below are a list of exceptions that do not fall within the above documents. Sections marked in gray are proposed amendments, and are pending discussion to approval/rejection.

Discussions will be had every other Friday at close of play to discuss/vote on whether the proposed amendment gets approved. In favour of keeping the standards as simple as possible - an amendment must have an approval rate of over 60%.

#### Variables
Variable names MUST be defined in camelCase

#### Methods

Chained methods MUST be on new lines, and be indented with one tab, as follows:

```
$email->from('foo@example.com')->to('bar@example.com')->subject('A great message')->send();
```

Becomes

```
$email->from('foo@example.com')
    ->to('bar@example.com')
    ->subject('A great message')
    ->send();
```

#### Spacing

Concatenation of string should be done without spaces, as follows.

```php
return $this->first_name.' '.$this->last_name;
```

Referencing array elements by their index should be done without 
spaces at the start and end of square brackets, as follows.

```php
$data[$key]
```

### Adhering to standards
It’s all well and good having a set standard outlined - but following it can be difficult unless you’re always thinking about following it.

There are a few methods of adhering to these standards which we will be implementing.

#### PhpStorm + PHP Code Sniffer
PhpStorm has support for PHP Sniffer, which enables live, in-IDE prompts to fix stylings. We can develop a custom setup to handle these extra rules, or at the least default it to PSR-2.

You can see Jetbrains’ guide to configuration [here](https://confluence.jetbrains.com/display/PhpStorm/PHP+Code+Sniffer+in+PhpStorm)

#### PhpStorm + PHP-CS-Fixer
A similar solution to the above is PHP CS Fixer. It’s not as easy to integrate live into your IDE but there are a number of guides to do so. The benefit of this one is that it’s the same engine that Style CI uses, which in turn ensures that there aren’t any unexpected PR blocks from the CI service.
