# 📖 Langley Foxall Open Source
## Background

Open source software and open standards are critical components of modern web applications and the software industry as a whole. This includes components of the web browsers, web servers, and operating systems used by millions daily.

We believe relying upon open standards and software has been fundamental to the success of the software industry as a whole. To aid in this, Langley Foxall is committed to giving back to the community. We try to contribute useful open source software, libraries, and other tools wherever possible. These packages are often used internally or as a part of our bespoke software solutions.

In fact, the page you are reading right now is part of just one of these open source projects.

## Our Open Source Projects

We love contributions and want our packages to help people, so if you have suggestions for improvements, please file
an issue on the relevant repository.

## Creating Open Source Projects

When creating open source software, we're aware that these projects can be used in systems that other developers build & rely on, because of this, we have rigid requirements for our OSS which help mitigate breaking changes from being introduced into stable versions of the public projects we release.

When a project reaches `v1.0.0` we have the following safe guards in place:

- When a project reaches `v1.0.0`, we stricly follow semantic versioning to ensure updates don't break existing implementations or expected functionality.
- A comprehensive test suite designed to ensure new code introduced doesn't break existing functionality and in turn, other developer's code.
- Travis CI ensures code changes don't break existing functionality by automatically running the test suite when code is changed, and StyleCI enforces our internal style guides to keep the project consistent and maintainable.
- The project is documented, so it's easy to use.

The above can't be guarenteed when using a version below `v1.0.0` as these will still be in development and subject to change.

##### PHP
* [PHP Mathematical Equation Evaluator](https://github.com/langleyfoxall/math_eval) - An evaluator that returns the 
result of a mathematical equation string.

##### Laravel
* [💸 Laravel Xero](https://github.com/langleyfoxall/xero-laravel) - An Eloquent-esque interface for the Xero PHP Wrapper
* [Laravel Modules](https://github.com/langleyfoxall/modules-laravel) - A package for building modular Laravel applications
* [Laravel Helpers](https://github.com/langleyfoxall/helpers-laravel) - A useful set of helper functions for use in Laravel
* [Laravel Boilerplate](https://github.com/langleyfoxall/laravel-boilerplate) - A prepared Laravel project that has 
common setup/packages included
* [🔒 Laravel NIST Password Rules](https://github.com/langleyfoxall/laravel-nist-password-rules) - A set of validation 
rules to ensure passwords adhere to a common security standard.

##### React
* [React Dynamic Data Table](https://github.com/langleyfoxall/react-dynamic-data-table) - A react table component that supports sortable columns, pagination, field mapping, data 
manipulation, and more.

##### Swift
* Formation - A form builder for Swift applications *COMING SOON*
